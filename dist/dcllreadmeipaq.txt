Accelr8 Technology Corporation
303 E. 17th Ave., Suite 108
Denver, CO 80203 USA
Phone: 303-863-8088
E-mail: info@accelr8.com
WWW: http://www.accelr8.com

Open DCL Lite v2.21 README (June 19, 2001)


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
We believe we are the best at what we do, and we hope this sample of our
work will help to spread the word that there is a viable alternative
to the paths often chosen: lengthy, costly rewrites from scratch which
frequently result in lost features and take huge amounts of testing,
or trying to find an "off the shelf" solution which will never do just
what you want and will ensure that all the previous investment in your
custom software is lost.  Make your software work first, then worry about
eliminating VMS-like features later if they bother you.

NOTE: Open DCL Lite is supplied free of charge with no warranty or support.
      No claim is made as to its fitness for any task, nor do we assume
      any liability for loss of data or other damages which result from
      the use of this product.  Please see the file LICENSE.TXT for
      more information.


Installation
============

Open DCL Lite is distributed in the tar format.
Copy the dcll_ipaq_linux.tar into /root on your iPAQ.
Then,

tar xf dcll_ipaq_linux.tar

This will place "dcll", "facil.dat", "messages.dat", and "litehelp.hlb" into
your /root directory, along with a script named "d" which will run DCL
Lite.  Simply type "./d" at a shell prompt.

