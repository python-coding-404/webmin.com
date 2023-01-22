---
title: "Webmin 1.330-1.140 release notes"
date: 2004-04-06
tags: ["changelog", "webmin-changelog"]
showtoc: true
---

- #### 1.140
    - Fixed a security hole that allowed any user to view the configuration of any module, even those that they should not have access to.
    - Fixed a security hole that could allow an attacker to lock valid users by sending a bogus username or password.

- #### 1.150
    - Updated the setup.sh script to use MD5 password encryption by default, on systems where Perl supports it.
    - Fixed a security hole in the `maketemp.pl` script, used to create the /tmp/.webmin directory at install time. If an un-trusted user creates this directory before Webmin is installed, he could create in it a symbolic link pointing to a critical file on the system, which would be overwritten when Webmin writes to the link filename (CVE bug CAN-2004-0559).
    - When PAM is used for Unix authentication, expired passwords are now detected and the user is prompted to select a new password (if this feature is enabled on the Webmin Configuration module).
    - Make all functions in `ui-lib.pl` themable, allowing themes to have more detailed control over modules that make use of this library.
    - Updated all modules to call `ui_print_header` instead of calling header and printing `<hr>`, so that themes can avoid the `<hr>`. Also updated the MSC theme to do this.

- #### 1.160
    - Added support for Solaris 10.
    - Included several additional translations for various languages and modules.
    - Added support for config- files that allow a range of OS version numbers, and used this to reduce the number of standard config files.

- #### 1.170
    - When installing a module from the command line, by it will be granted to the same users who receive new modules when Webmin is upgraded. By default, this is root and admin.
    - Added basic support for multiple root directories, so that Webmin modules can be separated into core and third-party on the filesystem.
    - When installing or upgrading Webmin, password timeouts are now enabled by default. This protects against brute-force password guessing attacks.

- #### 1.180
    - All subheadings have been reduced in size when using the default MSC theme.
    - All modules now use a new API for writing to configuration files, which ensures that the file does not get written to or truncated if the system is out of disk space.

- #### 1.200
    - On Solaris systems that support RBAC, available modules and access rights can now be derived from RBAC for selected users. This can be enabled on a per-user or per-module basic in the Webmin Users module.

- #### 1.210
    - Added a new Global ACL control option to limit a user to read-only mode. This does not yet support all modules, but in those that are supported any changes the user makes will simply not take effect.
    - Restarting of Webmin is now much faster in some modules that do not need a full configuration reload, due to the addition of a function that justs tells `miniserv.pl` to re-read its config file.

- #### 1.220
    - Added basic support for running Webmin on Windows system with ActiveState Perl installed. The new `setup.pl` install script must be used, as the setup.sh shell script cannot run on Windows.
    - Fixed a bug that could allow a remote attack if the option to use full PAM conversations is enabled.
    - Improved the Webmin RPM to not lose the /etc/webmin directory when upgrading from an RPM by another vendor (like Mandrake or DAG).

- #### 1.230
    - Replaced all calls to the crypt() function with new code that will use the Crypt::UnixCrypt Perl modules on systems for with crypt() is broken.

- #### 1.240
    - Fixed a possible security hole caused by a bug in Perl.

- #### 1.260
    - Proxy settings made in the Webmin Configuration module are passed on to programs Webmin calls via the `http_proxy` and `ftp_proxy` environment variables.
    - Added automatically created UTF-8 translations for simplified and traditional Chinese.

- #### 1.270
    - Updated almost all modules that use tables to use the new `ui_columns` functions. This allows themes to do highlighting when a row is moved over or selected.
    - Added a new 'Simple Blue' theme, which uses fewer images and does table row highlighting.
    - Changed the way that Webmin log diff files are stored, so that they are categorized by action and not all in one huge directory.

- #### 1.280
    - Fixed security holes that allow remote read access to any file on the server for which the path is known.

- #### 1.290
    - SELinux security contexts are preserved on files safely modified by Webmin's write-and-rename code.
    - Added xmlrpc.cgi program, which provides an XML-RPC interface to all Webmin module functions.
    - Tested and improved support for Fedora 5.

- #### 1.300
    - Fixed the rare bug about renaming the .webmintmp file.

- #### 1.310
    - Module configuration files can now be named based on the real operating system types, such as config-Ubuntu-Linux, which would be used in preference to config-debian-linux.
    - When a large file is uploaded, it is no longer read into memory by `miniserv.pl`.
    - Update the code that fetches mirror sites from Sourceforge, to handle their new website design.
    - Changed the default theme for all installs to the new framed blue theme.
    - Updated all rows of links (like select all, invert selection, add something) above tables to use a separator between links.
    - Added caching for sudo capable user checks, to avoid excessive slow calls to sudo.
    - Fixed a memory leak when running under ActiveState Perl on Windows.

- #### 1.320
    - Fixed XSS bugs in chooser.cgi.
    - If the operating system is upgraded after Webmin is installed, a button is displayed on the main page to update Webmin's view of the current OS.
    - Improved the tabs API to add an option to put a box around the visible tab, and whitespace around tabs.
    - If listening on all specified IP addresses fails, Webmin will fall back to accepting connections on any address.
    - All Module Config pages are now generating using new `ui-lib.pl` code, for easier theming.
    - Added a global access control option to set the Unix user the file browser lists directories as.

- #### 1.330
    - Added more `ui-lib.pl` functions for hidden page sections.
    - Fixed another XSS bug in chooser.cgi.
    - The Webmin function to get the system's hostname now reads a file instead of calling the hostname comment, which is faster.
    - Added an ACL option to the file chooser for additional directories to allow access to.
    - Changed the way sizes are displayed, to use a format like 1.32 GB or 8 kB.
    - Removed letter images (used by the old theme), and forced the standard header function to always use text titles.
    - Added support for Slam64 Linux.
