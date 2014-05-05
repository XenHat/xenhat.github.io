---
layout: post
title: "Compiling Second Life Viewers under Linux"
description: "Attempting to make something complicated a bit more KISS"
category: Linux
tags: []
---
{% include JB/setup %}

This page will gradually be converted to markdown format as I get to it...

Last Updated: Sun Mar 23 02:27:37 EDT 2014 — Fixed 64-bit command
I’m trying to make the most straightforward guide to compile Second life viewers on various GNU/Linux distributions. Package list for Arch Linux, Debian, Fedora 16/17, Gentoo and OpenSUSE 11 are available.

All we are going to use is a terminal and a text editor, very few mouse actions.

First, you need to grab the necessary programs required to compile the source code.

Please click the button corresponding to your distribution.

Debian/Ubuntu 32-bit
{% highlight bash %}
sudo apt-get install \
mercurial cmake build-essential bison
flex {libc6,libx11,libxrender}-dev \
{libxml2,libgl1-mesa,zlib1g,libssl}-dev \
{libogg,libpng12,libdbus-glib-1}-dev \
{libgtk2.0,libglu1-mesa}-dev \
libcloog-ppl0 python-boto python-pip -y

sudo pip install autobuild
{% endhighlight %}

Debian/Ubuntu 64-bit
See debian/Ubuntu 32bit, then;
{% highlight bash %}
sudo apt-get install gcc-4.7-multilib libx11-dev:i386 libxrender-dev:i386\
 libxext-dev:i386 libgl1-mesa-dev:i386 \
 libglu1-mesa-dev:i386 libgl1-mesa-dev:i386 mesa-common-dev:i386
sudo ln -s /usr/lib/i386-linux-gnu/libX11.so.6 /usr/lib/i386-linux-gnu/libX11.so
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
sudo ln -s /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17 /usr/lib/i386-linux-gnu/libstdc++.so
sudo ln -s /usr/lib/i386-linux-gnu/libXext.so.6 /usr/lib/i386-linux-gnu/libXext.so
sudo ln -s /usr/lib/i386-linux-gnu/libXrender.so.1 /usr/lib/i386-linux-gnu/libXrender.so
{% endhighlight %}

Fedora 16-17
{% highlight bash %}
sudo yum install nano bison flex glibc-devel libstdc++-devel  \\
libX11-devel mesa-libGL-devel libXrender-devel gcc-c++ mesa-libGLU-devel  \\
zlib-devel openssl-devel libogg-devel libpng-devel dbus-glib-devel  \\
atk-devel cairo-devel gtk2-devel glib2-devel pango-devel python-pip  \\
python-boto SDL-devel libXext-devel mercurial cmake make libxml2-devel
sudo pip-python install autobuild
{% endhighlight %}

Fedora x86_64 (64bit OS)
{% highlight bash %}
Install the packages for Fedora 16/17 (see above) then run:
sudo yum remove libogg-devel glib2-devel &&
sudo yum install bison flex cairo-devel.i686 dbus-glib-devel.i686  \\
glib2-devel.i686 glibc-devel.i686 atk-devel.i686  \\
gtk2-devel.i686 libogg-devel.i686 libpng-devel.i686  \\
libstdc++-devel.i686 libX11-devel.i686 libXext-devel.i686  \\
libXrender-devel.i686 mesa-libGL-devel.i686 mesa-libGLU-devel.i686  \\
openssl-devel.i686 pango-devel.i686 SDL-devel.i686 zlib-devel.i686  \\
libxml2-devel.i686
{% endhighlight %}

OpenSUSE
{% highlight bash %}
sudo zypper in mercurial cmake gcc-4.5 gcc45-c++ gcc-c++ bison flex  \\
glibc-devel libstdc++-devel xorg-x11-libX11-devel mesa-devel  \\
xorg-x11-libXrender-devel zlib-devel libopenssl-devel libpng12-devel  \\
libxml2-devel python-pip
&& sudo pip install autobuild
{% endhighlight %}

Gentoo
{% highlight bash %}
emerge -av mercurial cmake bison flex sys-libs/lib-compat  \\
media-libs/gstreamer dev-python/pip --autounmask-write

sudo pip install autobuild
You really want to compile SDL with USE=”X opengl” at least.
{% endhighlight %}

Arch Linux
{% highlight bash %}
sudo pacman -S gcc cmake base-devel bison flex glibc libx11 libxrender  \\
libxml2 mesa zlib openssl libogg libpng inetutils bc gtk2 glib2
yaourt -S python2
yaourt -S python2-boto
yaourt -S autobuild
Since Arch Linux uses python 3 as default, we have to force python 2…

sudo unlink /usr/bin/python
sudo ln -s /usr/bin/python2.7 /usr/bin/python
I know, it’s dirty, but it’s the only way it works.
{% endhighlight %}

Arch Linux X86_64
{% highlight bash %}
do the Arch Linux instructions above, then install these:
sudo pacman -S multilib-devel bison flex glibc
sudo pacman -S multilib/lib32-acl multilib/lib32-alsa-lib multilib/lib32-alsa-oss \
multilib/lib32-alsa-plugins multilib/lib32-atk multilib/lib32-attr \
multilib/lib32-bzip2 multilib/lib32-cairo multilib/lib32-celt \
multilib/lib32-dbus-core multilib/lib32-e2fsprogs multilib/lib32-expat \
multilib/lib32-flac multilib/lib32-fontconfig multilib/lib32-freetype2 \
multilib/lib32-gcc-libs multilib/lib32-gdk-pixbuf2 multilib/lib32-gettext \
multilib/lib32-giflib multilib/lib32-glew multilib/lib32-glib \
multilib/lib32-glib2 multilib/lib32-glibc multilib/lib32-gmp \
multilib/lib32-gnutls multilib/lib32-gtk multilib/lib32-gtk2 \
multilib/lib32-json-c multilib/lib32-keyutils multilib/lib32-krb5 \
multilib/lib32-lcms multilib/lib32-libao multilib/lib32-libasyncns \
multilib/lib32-libcanberra multilib/lib32-libcanberra-pulse \
multilib/lib32-libcap multilib/lib32-libcups multilib/lib32-libffi \
multilib/lib32-libgbm multilib/lib32-libgcrypt multilib/lib32-libgpg-error \
multilib/lib32-libice multilib/lib32-libidn multilib/lib32-libjpeg-turbo \
multilib/lib32-libldap multilib/lib32-libltdl multilib/lib32-libmikmod \
multilib/lib32-libmng multilib/lib32-libogg multilib/lib32-libpciaccess \
multilib/lib32-libphobos multilib/lib32-libpng multilib/lib32-libpulse \
multilib/lib32-libsamplerate multilib/lib32-libsm multilib/lib32-libsndfile \
multilib/lib32-libssh2 multilib/lib32-libstdc++5 multilib/lib32-libtiff \
multilib/lib32-libvorbis multilib/lib32-libx11 multilib/lib32-libxau \
multilib/lib32-libxcb multilib/lib32-libxcomposite \
multilib/lib32-libxcursor multilib/lib32-libxdamage \
multilib/lib32-libxdmcp multilib/lib32-libxext multilib/lib32-libxfixes \
multilib/lib32-libxft multilib/lib32-libxi multilib/lib32-libxinerama \
multilib/lib32-libxml2 multilib/lib32-libxmu multilib/lib32-libxrandr \
multilib/lib32-libxrender multilib/lib32-libxss multilib/lib32-libxt \
multilib/lib32-libxtst multilib/lib32-libxv multilib/lib32-libxvmc \
multilib/lib32-libxxf86vm multilib/lib32-mesa multilib/lib32-mesa-demos \
multilib/lib32-mpg123 multilib/lib32-ncurses multilib/lib32-nettle \
multilib/lib32-nvidia-utils multilib/lib32-openal multilib/lib32-openssl \
multilib/lib32-osmesa multilib/lib32-p11-kit multilib/lib32-pango \
multilib/lib32-pcre multilib/lib32-pixman multilib/lib32-qt4 \
multilib/lib32-readline multilib/lib32-sdl multilib/lib32-sdl_image \
multilib/lib32-sdl_ttf multilib/lib32-speex multilib/lib32-sqlite3 \
multilib/lib32-tdb multilib/lib32-util-linux multilib/lib32-v4l-utils \
multilib/lib32-xcb-util multilib/lib32-zlib
If you have a Nvidia graphic card, you’re going to need this:

sudo pacman -S lib32-nvidia-libgl
{% endhighlight %}

Now, you have to grab the source code.
First, let’s keep the home folder nicely organized and create a folder where all the source code will go (because when it’s all over the place it looks ugly and takes time to find stuff)
I will use Linden Lab’s Release channel viewer in this example, adapt if you want to compile a different viewer

{% highlight bash %}
mkdir -p /home/$USER/src/viewers/
cd /home/$USER/src/viewers/
hg clone https://bitbucket.org/lindenlab/viewer-release ll_release
{% endhighlight %}
These commands will create a folder called “src” (for SouRCe) and a sub-directory called “viewers” and download the viewer’s source code in it’s own sub folder.
Get a cup of coffee, it’ll take a while.
Welcome back.
Now, we’ll try compiling.
The autobuild system is pretty much straightforward:

{% highlight bash %}
cd /home/$USER/src/viewers/ll_release/
autobuild configure -c ReleaseOS -- -DLL_TESTS:BOOL=FALSE
autobuild build --no-configure
{% endhighlight %}

Take a sandwich. Or two. Or a full plate of them. It took 1 hour and a half to compile over here on an AMD Athlon64 II X2 3800+, and 15 minutes on an AMD Phenom II X6 1055T. Estimated to 10 minutes on FX-8350.
Welcome back.
Now, check if everything went right. Since this is the release channel, it should compile. if not, well, that’s unfortunate.
Once you made sure the viewer compiled sucessfully, extract the generated archive somewhere, example in your user directory:

{% highlight bash %}
tar xvaf build-linux-i686/newview/SecondLife*.tar.* -C /home/$USER/
{% endhighlight %}

Now run the viewer as usual;
{% highlight bash %}
cd /home/$USER/SecondLife*/
./secondlife
{% endhighlight %}

if it doesn’t crash, congratulations!
If it does, you probably did something wrong. Or a linden needs to be blamed. Or the world just ended.
————
Thanks Sythos (Altair Memo) for the amazing help to find the required libs and indications to fix the code myself back on Kirstens Viewer, as well as his patience for my errors. And my wicked computer and terrible luck.