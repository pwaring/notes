Gentoo
======

Updating a system
-----------------

    emerge --update --deep --with-bdeps=y --newuse @world


VirtualBox
----------

Create box:

    vagrant package --base vagrant-gentoo-x86 --output gentoo-x86.box
    
Add box:

    vagrant box add gentoo-x86 gentoo-x86.box

Install guest additions:

    emerge --ask app-emulation/virtualbox-guest-additions
    rc-update add virtualbox-guest-additions default

 * [Virtualbox guest (forum post)](http://forums.gentoo.org/viewtopic-p-7408372.html)
