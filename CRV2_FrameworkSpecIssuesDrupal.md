Drupal is a open-source content-management. It contains features common
to content management systems, including user account registration and
maintenance, menu management, RSS feeds, taxonomy, page layout
customization, and system administration.

Drupal runs on any environment that supports both a Web server capable
of running PHP 5.2, Apache, IIS web servers with latest release and a
database (such as MySQL 5.0 of higher, SQLite, PostgreSQL 8.3 or
Microsoft SQL Server) to store content and settings. Because of that
Drupal can be vulnerable to various security vulnerabilities to its
environment that it runs on. Code Reviewer should have some knowledge
into the configurations and versions of the component software used to
run Drupal.

Drupal Modules

  - Drupal also uses a large array of modules components that can come
    from various sources. Code reviewer needs to understand what modules
    the application is being deployed to production with and have some
    access to a risk assessment of that module and what security
    vulnerabilities it might present to the organization that is
    deploying Drupal.

Drupal policy on security vulnerability

  - Drupal's policy is to announce the nature of each security
    vulnerability once the fix is released.
  - Administrators of Drupal sites are automatically notified of these
    new releases via the Update Status module or via the Update Manager,
    depending on the release of Drupal.
  - Drupal maintains a security announcement mailing list, a history of
    all security advisories, a security team home page, and an RSS feed
    with the most recent security advisories.
  - Code Reviewers are strongly recommended to frequently visit with
    Drupal Security web page. <https://www.drupal.org/security>

Keep Up to date on Releases.

  - Code Reviewer needs to understand what version of Drupal and its
    underlying components are being used. Latest version of Drupal at
    the time of writing this book was Drupal 7.