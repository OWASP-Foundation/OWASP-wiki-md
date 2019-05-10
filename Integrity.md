Data and system integrity is one of the primary goals of security, which
is why we see it reflected in the common litany of C-I-A
(Confidentiality, Integrity and Availability). Within the STRIDE threat
modeling approach, tampering directly attacks information integrity and
controls preventing spoofing and repudiation support integrity
requirements.

Data integrity controls guard against improper information modification
or destruction, and includes ensuring information non-repudiation and
authenticity.

U.S. National Institute of Standards and Technology (NIST) Special
Publication 800-53 includes the following controls that address
integrity and may be directly reflected within software implementations:

  - Tamper resistance and detection (SA-18)
  - Transmission confidentiality and integrity (SC-8)
  - Protection of information at rest (SC-28)
  - Software, firmware and information integrity (SI-7)
  - Information input validation (SI-10)
  - Memory protection (SI-16)

Accuracy of data processing and transmissions is a critical business
requirement, both for decision support processes and for regulatory
compliance reasons (Sarbanes-Oxley).

ISO 27001:2013 includes controls related to correct processing within
applications in the System acquisition, development and maintenance
group.

1.  Hernan, S., Lambert, S., Ostwald, T., and Shostack, A. *Uncover
    Security Design Flaws Using the STRIDE Approach*. MSDN Magazine.
    Microsoft. (2006).
    <https://msdn.microsoft.com/en-us/magazine/cc163519.aspx>
2.  Joint Task Force Transformation Initiative. *Security and Privacy
    Controls for Federal Information Systems and Organizations*. Special
    Publication 800-53 revision 4. (2013) U.S. National Institute of
    Standards and Technology.
    <http://dx.doi.org/10.6028/NIST.SP.800-53r4>
3.  ISO/IEC 27001:2013. Wikipedia. Retrieved from
    <http://en.wikipedia.org/wiki/ISO/IEC_27001:2013> on 25 May 2015.