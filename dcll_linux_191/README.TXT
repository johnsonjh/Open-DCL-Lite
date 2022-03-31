Accelr8 Technology Corporation
303 E. 17th Ave., Suite 108
Denver, CO 80203 USA
Phone: 303-863-8088
E-mail: info@accelr8.com
WWW: http://www.accelr8.com

Open DCL Lite v1.90 README (December 23, 1998)


Introduction
============

Open DCL Lite is an emulation of the DCL command language interpreter
found on VMS systems.  In Unix terms it can be thought of as a "DCL shell".
It is important to note that most VMS commands do not have direct
equivalents on Unix or NT, and so this product rarely ends up executing a
native command to do the work.  For example, the formatting options and
the output of the Unix "ls" command are nothing at all like what you get
with the VMS "DIRECTORY" command, even though the purpose of each command is
essentially the same.  The product has internal code which implements each
command in a way which will feel much more "right" to a VMS devotee.  The
product also supports the mixing of DCL and native commands, so you can
choose whichever you like better.

Open DCL Lite was developed by Accelr8 Technology Corporation as a
way to increase awareness of its commercial Open DCL product and other
migration software.  Open DCL supports a much larger set of DCL commands
and lexical functions, systemwide logical names, indexed files, and more.

If you need to move applications and users from VMS to either Unix or NT,
Accelr8 can provide the tools and the expertise to get you there.

NOTE: Open DCL Lite is supplied free of charge with no warranty or support.
      No claim is made as to its fitness for any task, nor do we assume
      any liability for loss of data or other damages which result from
      the use of this product.  Please see the file LICENSE.TXT for
      more information.


Installation
============

DCL Lite is distributed as a tar file compressed with the gzip utility.
If your system does not have the gunzip command you will need to download
it from one of the many FTP sites which contain the GNU code archive.
One such location is ftp://prep.ai.mit.edu/pub/gnu/gzip-1.2.4.tar.gz.

First create a directory in which to install the product.  We suggest the
directory /opt/accelr8 if you have permission to create directories in /opt.
Any directory will work as long as it is added to your PATH environment
variable or a symbolic link to the "dcll" executable is added to a directory
in the PATH.

Copy the distribution file into the new directory (e.g. the Linux version
of Open DCL Lite is named dcl_lite_linux_190.tar.gz), and then uncompress
the tar file with gunzip:

gunzip dcl_lite_linux_190.tar.gz

Then extract the tarfile:

tar xf dcl_lite_linux_190.tar

(If you are using GNU tar you could also use the "tar xzf" command on
the gzipped tarfile and save a step)

If you wish to add a symbolic link so that the "dcll" command is found
in your current search path, use a command like this:

ln -s /opt/accelr8/dcll /usr/local/bin/dcll

This assumes that the product is installed in /opt/accelr8 and that the
directory /usr/local/bin is in your PATH.  If you do not create a link you
will need to update your PATH environment variable accordingly.

Another alternative to symbolic linking or altering your PATH would
be to copy the "dcll" executable into a directory which is in your PATH,
and then you would need to set up a new environment variable named DCLLITE
which equates to the directory where the files were extracted.  For example:

export DCLLITE=/usr/local/accelr8

In this example, the product is installed in the /usr/local/accelr8 directory.

PLEASE NOTE: The Linux world is currently going through a transition from
             one C runtime libary to another (libc5 to glibc2).  The "dcll"
             executable uses the older libc5 library.  The first release
             of Open DCL Lite did not gracefully handle the condition
             of being run on a system without the needed library.  That
             release can be identified by a "1998-345" in the version
             number banner printed when the command is invoked.
             The current version is marked "1998-357" and should print
             a message like this if there is a problem:

             Your system does not seem to have usable libc5 libraries.
             Please try the glibc2 version instead.

             If you get this message you should replace the "dcll"
             command with the "dcll.glibc2" file.  To do this, use
             the following Linux command:

             mv dcll.glibc2 dcll


Using Open DCL Lite
===================

Open DCL Lite is invoked by typing the command "dcll".  You can see a list
of the supported commands by typing the command "HELP" at the "A8$" prompt.
Supported lexical functions can also be found there under the heading
"Lexicals".

In this Lite version the logical name support does not include the sharing
of logical name tables between processes.  In order to avoid any implication
that such sharing exists, the LNM$GROUP and LNM$SYSTEM logical name tables
are not available.  If you need logical name table sharing you will need
the commercial version.

Open DCL Lite supports the sylogin.com and login.com startup command
procedures.  The sylogin.com file should be placed in the installation
directory and should include any startup commands which are to be executed
for all users on the system.  The login.com file should be placed in
the user's home directory and contain personal startup commands.

With the default settings the Open DCL Lite product assumes that any
command not recognized as being a DCL command is in fact a native command.
So, typing "ls" will work at the A8$ prompt.  If you wish to invoke a
native command which conflicts with the name of a DCL command, simply
add the command "SHELL" at the beginning of the line.  For example, suppose
that you have a Unix "dir" command on your system (many Linux systems do) and
you want to use it instead of the DCL version.  You would use a command
like this:

A8$ shell dir

To configure Open DCL to always use the native "dir" you could add the
following line to your sylogin.com our login.com:

$ DIR :== shell dir

The dcll command supports two options inspired by Unix shells.  The first
is the "-c" option, which invokes the DCL interpreter to execute a
single command, for example:

$ dcll -c "SHOW USERS"

The other option instructs the dcll command to execute a single command
procedure.  To do this, simply specify the name of the command procedure
as the only argument to the command, for example:

$ dcll myprocedure.com

This product does not support use as a login shell.  Use the command
"exec dcll" from a .profile or .login shell startup script if you want
DCL Lite to replace your default Unix shell.

