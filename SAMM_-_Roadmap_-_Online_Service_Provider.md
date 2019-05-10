# Online Service Provider

<div style="width:48%; float:right;">

![SAMM-Roadmap-OSP.png](SAMM-Roadmap-OSP.png "SAMM-Roadmap-OSP.png")

</div>

<div style="width:48%; float:left; padding-right:10px;">

## Rationale

An Online Services Provider involves the core business function of
building web applications and other network-accessible interfaces.

Initial drivers to validate the overall soundness of design without
stifling innovation lead to early concentration on Design Review and
Security Testing activities.

Since critical systems will be network-facing, Environment Hardening
activities are also added early and ramped over time to account for
risks from the hosted environment.

Though it can vary based on the core business of the organizations,
Policy & Compliance activities should be started early and then advanced
according to the criticality of external compliance drivers.

As the organization matures, activities from Threat Assessment, Security
Requirements, and Secure Architecture are slowly added to help bolster
proactive security after some baseline expectations for security have
been established.

## Additional Considerations

### Outsourced Development

For organizations using external development resources, restrictions on
code access typically leads to prioritization of Security Requirements
activities instead of Code Review activities. Additionally, advancing
Threat Assessment in earlier phases would allow the organization to
better clarify security needs to the outsourced developers. Since
expertise on software configuration will generally be strongest within
the outsourced group, contracts should be constructed to account for the
activities related to Operational Enablement.

### Online Payment Processing

Organizations required to be in compliance with the Payment Card
Industry Data Security Standard (PCI-DSS) or other online payment
standards should place activities from Policy & Compliance in earlier
phases of the roadmap. This allows the organization to opportunistically
establish activities that ensure compliance and enable the future
roadmap to be tailored accordingly.

### Web Services Platforms

For organizations building web services platforms, design errors can
carry additional risks and be more costly to mitigate. Therefore,
activities from Threat Assessment, Security Requirements, and Secure
Architecture should be placed in earlier phases of the roadmap.

### Organizations Grown by Acquisition

In an organization grown by acquisition, there can often be several
project teams following different development models with varying
degrees of security-related activities incorporated. An organization
such as this may require a separate roadmap for each division or project
team to account for varying starting points as well as project-specific
concerns if a variety of software types are being developed.

</div>

<div style="float:left; width:100%;">




\----

-----

### Additional Resources

</div>

__NOTOC__ __NOEDITSECTION__