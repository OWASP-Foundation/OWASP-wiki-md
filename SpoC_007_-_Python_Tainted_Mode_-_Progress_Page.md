***[Back to Python Tainted Mode Main
Page](http://www.owasp.org/index.php/SpoC_007_-_Python_Tainted_Mode)***

## Documentation, accomplished objectives and deliveries for OWASP Spring of Code 2007

### Documentation

[Python Tainted Mode Documentation,
version 1.0.0](http://zigzag.lvk.cs.msu.su/~petand/Py_TM/TaintedMode.pdf)

### Accomplished objectives at 1st of November 2007

  - **\[100%\]** Formalize Tainted Mode paradigm.
  - **\[100%\]** Add 'tainted' flag field to str and unicode Python
    types that tracks data taintedness.
  - **\[100%\]** Provide propagation of 'tainted' flag throughout
    strings interaction (concatenation, substring, etc.).
  - **\[100%\]** Add support for logging of Python programms traces. For
    debug and analysys purposes only.
  - **\[100%\]** Add support for analysys of callable objects
    invocation. Callable object is classified as input, filter, critical
    or other.
  - **\[100%\]** Add support for analysys of retrieving data from object
    fields. For example, data from mod_python's
    mp_request.headers_in\["Accept"\] should be treated as tainted.
  - **\[100%\]** Add support for exceptions raising after tainted data
    is passed into critical callable objects. This would be "Classical
    Tainted Mode".
  - **\[100%\]** Add support for logging of tainted arguments passed
    into critical callable objects. This would be "Tainted Mode with
    Logging".
  - **\[100%\]** Perform review of most popular Python frameworks in
    order to complete configuration profiles that contain signature of
    input, filter and critical callable objects for each framework.
  - **\[100%\]** Perform testing and state proposals for future work.

### As for Python Tainted Mode delivery

[Python Tainted Mode with applied
patch](http://zigzag.lvk.cs.msu.su/~petand/Py_TM/Python-2.4.4.zip)

[Python Tainted Mode patch only
files](http://zigzag.lvk.cs.msu.su/~petand/Py_TM/Python-patch-2.4.4.zip)

[Python Tainted Mode
documentation](http://zigzag.lvk.cs.msu.su/~petand/Py_TM/TaintedMode.pdf)

***'[Back to Python Tainted Mode Main
Page](http://www.owasp.org/index.php/SpoC_007_-_Python_Tainted_Mode)***'