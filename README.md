Do Not Eat The Dead
===================

This is a little tool to generate a ~/.XCompose file which does not
consume dead keys unless they are part of a valid composed characted.

By default, when you configure your keyboard in X11 to use one of the
international variants [2] you can compose characters using dead keys
-- for example, _~n_ becomes _ñ_.  However, _~p_ is meaningless, so
doesn't output anything.  This is jarring if you're used to dead keys
as they are implemented on Microsoft Windows, where _~p_ would just
output _~p_.

X11 can easily be configured to output _~p_ for _~p_, but it would be
a lot of work to manually write a .XCompose file for every possible
invalid combination.  So I've cobbled together a short python script
to do this task, you can use it like this:

         ./do-not-eat-the-dead > ~/.XCompose

Obviously you may want to make a backup of your previous XCompose
file.  The script requires python and has only been tested with python
2.7.

[1] Like this:
    setxkbmap -layout us -variant intl -option ctrl:nocaps
    setxkbmap -layout us -variant dvorak-intl -option ctrl:nocaps


Configuring GTK/KDE
===================

~/.XCompose is used by the X Input Method, so in order for the file to
work you will have to make sure your applications use the correct
input method.  Add the following environment settings to your
~/.xinitrc or ~/.xsessionrc:

    export DISABLE_IMSETTINGS=yes
    export GTK_IM_MODULE=xim
    export QT_IM_MODULE=xim


License
=======

Copyright 2012, Kuno Woudt <kuno@frob.nl>

Licensed under the Apache License, Version 2.0 (the "License"); you
may not use this file except in compliance with the License.  You may
obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
implied. See the License for the specific language governing
permissions and limitations under the License.
