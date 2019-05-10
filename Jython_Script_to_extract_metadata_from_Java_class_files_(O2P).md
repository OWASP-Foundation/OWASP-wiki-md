This is the current code that is executed using Jython that creates an
XML file with the Java metatag information. Note that this was my
(Dinis) first ever Python script so I was busking it all the way (while
basterdizing John's code :)  )

    import sys
    from javassist.bytecode import *
    from java.io import *

    #<begin of Dinis Changes>

    import java
    import os

    ' global vars'
    true = 1
    false = 0


    def createXmlElement(name, parameters, innerXml,indent,allContentInSameLine, encodeInnerXml) :
        if encodeInnerXml:
            innerXml = innerXml.replace("&","&amp;").replace("<","&lt;").replace(">","&gt;")

        parametersTextValue = ""
        for parameter in parameters:
            parameterName = parameter
    #        if  isinstance (parameters[parameter],int):
    #            parameterValue += parameters[parameter]
    #        else:
            parameterValue = parameters[parameter].replace("\"", "&quot;").replace("<","&lt;").replace(">","&gt;").replace("&","&amp;")
            parametersTextValue += " %s = \"%s\"" % (parameter, parameterValue)

        beginTagValue = name + parametersTextValue
        engTagValue = name

        if innerXml == "":
            return ("\n%s<%s/>" %               ("\t"*indent,beginTagValue) )

        if allContentInSameLine:
            return ("\n%s<%s>%s</%s>" %         ("\t"*indent,beginTagValue, innerXml, engTagValue) )

        return ("\n%s<%s>%s%s\n%s</%s>" %   ("\t"*indent, beginTagValue ,"\t"*(indent+1), innerXml,"\t"*indent, engTagValue) )


    def getAnnotationInfo(xmlNodeName,annotations):
        annotationsInfo = ""
        for annotation in annotations:
            if annotation == None:
                annotationsInfo += createXmlElement(xmlNodeName,{},  "" ,3,false,false)
            else:
                annotationParams = {"typeName":annotation.typeName,"toString":annotation.toString()}

                ' check if there are members in this attribute'
                annotationMembers = ""
                if annotation.memberNames != None:
                    for annotationMemberName in annotation.memberNames:
                        annotationMember = {"memberName":annotationMemberName,"memberValue":annotation.getMemberValue(annotationMemberName).toString()}
                        annotationMembers += createXmlElement("member", annotationMember,"",4,true,true)

                annotationsInfo +=createXmlElement(xmlNodeName, annotationParams, annotationMembers,3,false,false)

        return annotationsInfo

    def getAttributeInfo(attributes):
        attributeInfo = ""
        for attribute in attributes:
            if attribute == None:
                annotationsInfo += createXmlElement("attribute",{},  "" ,4,false,false)
            else:
                attributeParams = {"toString":attribute.toString(), "typeName": java.lang.Class.getName(attribute.getClass()),"name":attribute.name}
                'if there are annotations we need to add them individually'
                if hasattr(attribute,"numAnnotations"):
                    attributeAnnotations = getAnnotationInfo("annotation",attribute.getAnnotations())
                    attributeInfo += createXmlElement("attribute",attributeParams,  attributeAnnotations ,2,false,false)
                else:
                    attributeInfo += createXmlElement("attribute", attributeParams, "" ,2,true, true)

        return attributeInfo

    def getMethodsCalled(method):
        methodsCalled = ""
        codeAttribute = method.getCodeAttribute()
        if (codeAttribute == None):
            return methodsCalled;
        constPool = codeAttribute.getConstPool();
        codeIterator =  method.getCodeAttribute().iterator()
        while (codeIterator.hasNext()):
        next = codeIterator.next()
        byteCodeInst = codeAttribute.getCode()[next]
        if (byteCodeInst == -73 or byteCodeInst == -74):    # method call
            methodCalled_Index = 0x000000FF & codeAttribute.getCode()[next+2] # need to convert signed byte value into an unsigned value
            methodCalled_Index += (0x000000FF & codeAttribute.getCode()[next+1]) * 0x100
            methodCalled_Class = constPool.getMethodrefClassName(methodCalled_Index)
                    methodCalled_Name = constPool.getMethodrefName(methodCalled_Index)
                    methodCalled_Descriptor = constPool.getUtf8Info(constPool.getNameAndTypeDescriptor(constPool.getMethodrefNameAndType(methodCalled_Index)))
                    methodCalled_LineNumber = method.getLineNumber(next).__str__()

                    methodCalled_Signature = methodCalled_Class + "." + methodCalled_Name  + methodCalled_Descriptor;
                    xmlElementAttributes = {"lineNumber":methodCalled_LineNumber,"class":methodCalled_Class,"name":methodCalled_Name,"descriptor":methodCalled_Descriptor,"signature":methodCalled_Signature}
                    methodsCalled += createXmlElement("methodCalled",  xmlElementAttributes,"",5,True,True)

        if (byteCodeInst == -71):       # interface call
            methodCalled_Index = 0x000000FF &  codeAttribute.getCode()[next+2];
            methodCalled_Index += (0x000000FF & codeAttribute.getCode()[next+1]) * 0x100

            methodCalled_Class = constPool.getInterfaceMethodrefClassName(methodCalled_Index)
            methodCalled_Name = constPool.getInterfaceMethodrefName(methodCalled_Index)
            methodCalled_Descriptor = constPool.getUtf8Info(constPool.getNameAndTypeDescriptor(constPool.getInterfaceMethodrefNameAndType(methodCalled_Index)))
            methodCalled_LineNumber = method.getLineNumber(next).__str__()

            methodCalled_Signature = methodCalled_Class + "." + methodCalled_Name  + methodCalled_Descriptor;
                    xmlElementAttributes = {"lineNumber":methodCalled_LineNumber,"class":methodCalled_Class,"name":methodCalled_Name,"descriptor":methodCalled_Descriptor,"signature":methodCalled_Signature}
            methodsCalled += createXmlElement("methodCalled",  xmlElementAttributes,"",5,True,True)

        return methodsCalled

    def getSuperClassAndInterfaces(classObject):
        #print "superclass: " + classObject.getSuperclass()
        superClassAndInterfaces = createXmlElement("superclass", {"name":classObject.getSuperclass()},"",2,true,false)
        for _interface in classObject.getInterfaces():
        #   print "interface: " + _interface
            superClassAndInterfaces += createXmlElement("interface", {"name":_interface},"",2,true,false)
        return superClassAndInterfaces;

    def getClassinfo(path, attributeParser):

        classObject = attributeParser._acquireClassFile(path)

        classAttributes = getAttributeInfo(attributeParser.getClassAttributes(path))
        superClassAndInterfaces = getSuperClassAndInterfaces(classObject)
        'calculate methods'
        methodsNodes = getMethodsinfo(path,attributeParser)
        'methodsNode = createXmlElement("methods",methodsChildNodes,2,true,false)'

        'put it all together'

        classChildNodes = classAttributes + superClassAndInterfaces + methodsNodes
        sourceFile = os.path.dirname(classObject.getName().replace('.', '\\')) +"\\"
        if classObject.getSourceFile() != None:
             sourceFile = sourceFile + classObject.getSourceFile();

        classNode = createXmlElement("class", {"sourceFile":sourceFile,"name":classObject.name} ,classChildNodes,1,false,false);

        return classNode , classObject


    def getMethodsinfo(path, attributeParser):
        methods = attributeParser._acquireClassFile(path).getMethods()
        xmlContent = ""
        ' add methods details'
        for method in methods:
            'xmlContent+="\n<M>" + method.toString() + "</M>"'

            xmlNodeParams = {"name": method.name, "descriptor": method.descriptor, "lineNumber": method.getLineNumber(0).__str__()}

            xmlNodeInnerXml = getAttributeInfo(attributeParser.getMethodAttributes(path,method.name, method.descriptor))

            xmlNodeInnerXml+= getAnnotationInfo("parameterAnnotation",attributeParser.getMethodParametersAttributes(path,method.name, method.descriptor))

            xmlNodeInnerXml += getMethodsCalled(method)

            xmlContent += createXmlElement("method",xmlNodeParams ,xmlNodeInnerXml,2,false, false)

        return xmlContent

    def canProcessFile(path):
        return AttributeParser()._acquireClassFile(path) != None

    def createXmlFile(resultsFolder, path):
        print "\n Creating XmlFile with Attribute info for: " + path
        if (canProcessFile(path)):
            attributeParser = AttributeParser()

            classNode ,classObject = getClassinfo(path,attributeParser)
            xmlContent = createXmlElement("JavaAttributeMappings", [],classNode,0,false, false)


            xmlFileName = resultsFolder +"\\"+classObject.name +".JavaAttributes.xml"
            xmlFile = open(xmlFileName,"w")
            xmlFile.write(xmlContent)
            xmlFile.close

        'print "Xml file created: " + xmlFileName'

    def createXmlFileForDir(resultsFolder, dirPath):
        print "\n Creating XmlFile with Attribute info for directory : " + dirPath + "\n"
        for root, dirs, files in os.walk(dirPath):
            for file in files:
                if file.endswith(".class"):
                    createXmlFile(resultsFolder, root + "\\" + file)

    '</begin of Dinis Changes>'



    ' Below is John\'s original code'

    class AttributeParser(object):
        '''This class uses a bytecode parsing approach to implement query of
           class, method, method parameter, and field annotations on a
           path-to-classfile target.

           Dependencies include:
           jython 2.5.0 - http://bugs.jython.org (Python Interpreter written in
                          Java that has an embedded Java VM)

           javassist-3.11.0 - http://www.csg.is.titech.ac.jp/~chiba/javassist/ (
                          Java bytecode manipulation tool, that supports JRE 1.6)

           Execute the tool using the following:
           java  -jar jython.jar  -Dpython.path=./javassist.jar

           >>>import Annotations
           >>>ap = Annotations.AttributeParser()
           >>>help(ap)

           Author: John Steven (jsteven@cigital.com)
           Created on: 07-10-09
           LastChanged: $LastChangedDate$

           Modified by: Dinis Cruz (dinis.cruz@ouncelabs.com
           Modified on: 11-10-09
           Where: places where the quality of the Python code dramatically drops :)
        '''

        def getClassAttributes(self, path_to_clazz):
            '''getClassAttributes() returns a list of annotations associated with the
               class definition.

               path_to_clazz : str - the absolute path to the class file to interrogate
               returns : [] - list of zero or more class annotations.
               returns : None - Error finding/loading/parsing class file data
            '''
            cf = self._acquireClassFile(path_to_clazz)
            if cf == None: return None

            attributes_to_return = list()

            try:
                attributes = cf.getAttributes()
                for attribute in attributes:
                    if isinstance(attribute, SourceFileAttribute):
                        pass # Explicitly punt this attribute type
                    elif isinstance(attribute, InnerClassesAttribute):
                        pass # Explicitly punt this attribute type
                    else:
                        attributes_to_return.append(attribute)

                return attributes_to_return

            except:
                print 'WARNING - %s: encountered %s %s getting attributes in %s' %\
                      (self.__class__.__name__, sys.exc_info()[0],
                       sys.exc_info()[1], path_to_clazz)
                return None

        def getFieldAttributes(self, path_to_clazz, field_name):
            '''getFieldAttributes() return a list of annotations associated with a
               field within the class definition.

               path_to_clazz : str - the absolute path to the class file to interrogate
               field_name : str - the name of the class' field the query targets
               returns : [] - list of zero or more field annotations.
               returns : None - Error finding/loading/parsing class file data
            '''
            cf = self._acquireClassFile(path_to_clazz)
            if cf == None: return None

            try:
                return list(f.getAttributes()[0] for f in cf.getFields() \
                                                   if str(f.getName()) == field_name)
            except:
                print 'WARNING - %s: encountered %s %s getting %s\'s attributes for %s' %\
                      (self.__name__, sys.exc_info()[0], sys.exc_info()[1], field_name,
                       path_to_clazz)
                return None

        def getMethodAttributes(self, path_to_clazz, method_name, signature=None):
            '''getMethodAttributes() return a list of annotations associated with (a)
               method(s) within the class definition.

               path_to_clazz : str - the absolute path to the class file to interrogate
               method_name : str - the name of the class' field the query targets
               signature : Boolean - whether or not to match methods by full signature
                           rather than just name (useful if method is overloaded)
               returns : [] - list of zero or more method annotations.
               returns : None - Error finding/loading/parsing class file data
            '''
            return self.__getMethodAttributesImpl(path_to_clazz, method_name,
                                                  parameters=False, signature=None)

            def getMethodParametersAttributes(self, path_to_clazz, method_name,
                                         signature=None):
                    '''getMethodParametersAttributes() return a list of annotations associated
               with (a) method's parameters.

               path_to_clazz : str - the absolute path to the class file to interrogate
               method_name : str - the name of the class' field the query targets
               signature : Boolean - whether or not to match methods by full signature
                           rather than just name (useful if method is overloaded)
               returns : [] - a list of the annotations associated with each parameter
                              within the method signture. Those not bearing annotations
                              will have a 'None' Entry
               returns : None - Error finding/loading/parsing class file data
            '''
            return self.__getMethodAttributesImpl(path_to_clazz, method_name,
                                                  parameters=True, signature=None)

        def __getMethodAttributesImpl(self, path_to_clazz, method_name,
                                    signature=None, parameters=False):
            '''Private getMethodAttributesImpl() - configures attribute-type matching
               function and then computes work of matching methods, and pulling
               annotations (associated with parameters) as appropriate.
            '''
            def switchAnnotationType(interestInParams):
                if interestInParams:
                    return lambda at: isinstance(at, ParameterAnnotationsAttribute)
                else:
                    return lambda at: not isinstance(at, ParameterAnnotationsAttribute)

            cf = self._acquireClassFile(path_to_clazz)
            if cf == None: return None

            attributes_to_return = list()
            filterFn = switchAnnotationType(parameters)

            try:
                for method in cf.getMethods():
                    if self.__matchMethod(method_name, signature, method):
                        for attribute in (attribute for attribute in method.getAttributes()\
                                          if filterFn(attribute)):
                                                    if isinstance(attribute, CodeAttribute):
                                pass # Explicitly punt this attribute type
                            elif isinstance(attribute, ParameterAnnotationsAttribute):
                                for annotation in attribute.getAnnotations():
                                    if len(annotation) == 0:
                                        attributes_to_return.append(None)
                                    else:
                                        attributes_to_return.append(annotation.pop())
                            else:
                                attributes_to_return.append(attribute)

                return attributes_to_return

            except:
                print 'WARNING - %s: encountered %s %s getting %s\'s attributes for %s' %\
                      (self.__class__.__name__, sys.exc_info()[0], sys.exc_info()[1],\
                       method_name, path_to_clazz)
                return None

        def __matchMethod(self, method_name, signature, method):
            '''Private matchMethod() - handles method matching by name (and if supplied
               by full Java bytecode method signature).

               method_name : str - the name of the method without parans, params, RV,
                             FQ class name, etc. 'foo' for 'foo()'
               signature : str - bytecode formatted method signature (IE:
                           (Ljava/lang/string;)V' In the case that name-only matching
                           is desired, the callers should pass 'None' for this param.
               method : javassist.bytecode.Method object, the reversed Method object.

               returns : Boolean - True, the method matches, false otherwise.
            '''
            try:
                if signature == None:
                    return method_name == method.getName()
                elif method_name == method.getName():
                    return signature == method.getDescriptor()
                else:
                    return False
            except:
                print 'WARNING - %s: Failure parsing methods %s %s' \
                       %(self.__class__.__name__, sys.exc_info()[0], sys.exc_info()[1])
                return False

        def _acquireClassFile(self, path_to_clazz):
            '''semi-private acquireClassFile() - method designed as helper function to
               getXXXAttribute() functions, but also servese useful in unit testing b/c
               this methods returns the javassist.bytecode.ClassFile object which
               represents the fully parsed, reversed class file.

               path_to_clazz : str - the absolute path to the class file to interrogate
               returns : javassist.bytecode.ClassFile - Revered Java Class file
            '''
            try:
                dis = DataInputStream(BufferedInputStream(FileInputStream(path_to_clazz)))
                return ClassFile(dis)
            except:
                            ''' the code throws the error:
                                  AttributeError: 'AttributeParser' object has no attribute '__name__'
                            '''
                '''print 'WARNING - %s: encountered %s %s getting %s' %\
                      (self.__name__, sys.exc_info()[0], sys.exc_info()[1], path_to_clazz)'''
                print 'ERROR - encountered %s %s getting %s' %\
                      (sys.exc_info()[0], sys.exc_info()[1], path_to_clazz)
                return None

    ' DC Code'
    'createXmlFile(path)'

    errormessage = " The first argument must be the results folder and the 2nd argument must either be the target class or the target folder\n\n"

    if sys.argv.__len__() != 3:
        print "\n\n Error: You need to provide two parameters." + errormessage
    else:
        resultsFolder =  sys.argv[1]
        targetClassFileOrFolder = sys.argv[2]

        print "resultsFolder: " +  resultsFolder
        print "targetClassFileOrFolder: " +  targetClassFileOrFolder

        if (os.path.isdir(resultsFolder) and (os.path.isdir(targetClassFileOrFolder) or os.path.isfile(targetClassFileOrFolder))):
            if os.path.isdir(targetClassFileOrFolder):
                createXmlFileForDir(resultsFolder, targetClassFileOrFolder)
            elif targetClassFileOrFolder.endswith(".class"):
                createXmlFile(resultsFolder, targetClassFileOrFolder)
            else:
                print "\n\n File provided must be of extension .class:"
        else:
            print "\n\n Error with the arguments supplied:" + errormessage


    #targetFile = "E:\\O2\_Bin_(O2_Binaries)\\O2_Cmd_SpringMvc\_UnitTests\\TestFiles\\EditOwnerForm.class"
    #createXmlFile("C:\\O2", targetFile)



[Category:OWASP_O2_Platform](Category:OWASP_O2_Platform "wikilink")