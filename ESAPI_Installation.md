Installer Goals:

  - Essentially a one click install process
  - Download an installer, that is reasonably small
      - Could also provide a standalone installer, but this would be
        HUGE, and not sure about the licensing issues of bundling all
        this together
  - Have the installer download all the components it needs from the
    internet (kind of like what Maven does)
  - Have this be completely standalone, so it doesn't depend on anything
    on the current users computer
      - This includes java, eclipse, etc. - So it will take a while, but
        it will make it 'really' easy
  - Have a "how to" pop up at the end, that says what to do next (and
    maybe points to a wiki page as well with the same or more info)
      - How to build the software
      - Explanation of where the code repository is (since the installer
        should make this essentially invisible)
      - How to run the SwingSet
      - Where to get more information about ESAPI and its documentation