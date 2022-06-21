# apt & dpkg
*   **apt** stands for Advanced Package Tool (not to be confused with Aptitude).  It doesn’t deal with ‘deb‘ package and works directly, but works with ‘deb‘ archive from the location specified in the “/etc/apt/sources.list” file.
*   It combines the most frequently used commands from the apt-get and apt-cache tools with different default values of some options.
*   **dpkg** is a tool to install, build, remove and manage Debian packages

Code Examples: 

*   **Installing** packages 

    sudo apt install <package_name>[=version_number] 
    or 
    sudo dpkg -i <.deb package>

If for some reason you want to install a package but don't want to upgrade it once it is installed

    sudo apt install <package_name> --no-upgrade

This command searches the repositories and installs the build dependencies for <package\_name>. If the package is not in the repositories it will return an error.

    apt-get build-dep <package_name>

\[Common Error\] : E: You must put some 'deb-src' URIs in your sources.list  
Solution: \[Works in Ubuntu 20.04\] 

    sudo cp /etc/apt/sources.list /etc/apt/sources.list~
    sudo sed -Ei 's/^# deb-src /deb-src /' /etc/apt/sources.list
    sudo apt-get update

*   **Removing** packages 

    sudo apt remove PACKAGE1 PACKAGE2 ...

‘remove’ command only uninstalls packages, leaves behind configuration files. To remove including config files, use 

    sudo apt purge <package_name> 

*   **Updating** package index

    sudo apt update 

*   **Upgrading packages**: All packages upgraded by default. Does not upgrade packages that require removal of installed packages  

    sudo apt upgrade <OPTIONAL_PACKAGE_NAME> 

Full-upgrade of packages: Removes packages if that is needed to upgrade the whole system. 

    sudo apt full-upgrade 

*   **Listing Packages**: lists all available, installed and upgradeable packages 

    sudo apt list 

To list only installed packages: 

    sudo apt list --installed 

To list upgradeable packages may be useful before actually upgrading them 

    sudo apt list --upgradeable

To list all packages available for your system 

    sudo apt list --all-versions

To list files in any .deb package: 

    sudo dpkg -c <path_to_deb>

To list files in package <package\_name> : 

    sudo dpkg -L <package_name>

*   **Searching** Packages in apt repo: 

    sudo apt search PACKAGE_NAME
    or
    sudo apt-cache search <package_name>
    or
    sudo dpkg -l *<search_term>*

*   **Getting package information** (dependencies, installation size, package source, etc) might be useful before installing or removing them 

    sudo apt show <package_name>
    or
    sudo dpkg --print-avail <package_name>

*   **Auto-cleaning** installed deb packages from /var/cache/apt/archives

    apt-get autoclean