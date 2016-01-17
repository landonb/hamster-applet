############################
Hamster Time Tracking Applet
############################

A tweak of the Hamster `GNOME <https://www.gnome.org/>`__ applet.

- The Overview dialog defaults to showing the daily summary, rather than then weekly.

  - This makes it easier to see the current day's activities when you open the Overview.
    
    - You don't have to scroll the dialog to the bottom every time you open it.

- Show three decimal places in Totals when one or more Activities is selected.

  - The latter makes it easy for me to fill out my employer's daily time sheets with more accurate numbers.

    - A tenth of an hour is only six minutes, but minutes count! =)

Using this fork
---------------

Install hamster 2.9 packages from Ubuntu and then copy over a few files.

(I'm lazy and didn't package this as a standalone project.)

.. code-block:: bash

    pkill -f hamster-service
    pkill -f hamster-windows-service

    sudo apt-get install -y hamster-applet hamster-indicator

    cd path/to/somewhere
    git clone https://github.com/landonb/hamster-applet

    sudo /bin/cp -a \
        /usr/share/pyshared/hamster/overview.py \
        /usr/share/pyshared/hamster/overview.py.ORIG
    sudo /bin/cp -a \
        /usr/share/pyshared/hamster/overview_totals.py \
        /usr/share/pyshared/hamster/overview_totals.py.ORIG

    sudo /bin/cp -af \
        hamster-applet/src/hamster/overview.py \
        /usr/share/pyshared/hamster/overview.py
    sudo /bin/cp -af \
        hamster-applet/src/hamster/overview_totals.py \
        /usr/share/pyshared/hamster/overview_totals.py

    hamster-indicator &

Regarding Hamster 3.x
---------------------

I tried the newer (3.x) hamster from https://github.com/projecthamster/hamster,
but I didn't like it.

- I installed it by adding the ``ppa:dylanmccall/hamster-time-tracker-git-daily``
  aptitude repository and installing ``hamster-time-tracker``.

Some reactions:

- The Overview dialog is less useful in 3.x -- it only shows weekly activity,
  with no option to show daily or monthly activity.

- The Statistics display is no longer its own tab but a drawer that slides
  up from the bottom of the dialog, and there's no longer a summary time
  displayed for each task! (So I can't use the Statistics display to fill
  out my daily time sheet for work.)
  
- I'm not sure why these features were removed, but it feels like a step
  backward for the project.

I also tried installing the new applet from
https://github.com/projecthamster/shell-extension,
but I could not get it to run in `MATE <http://mate-desktop.com/>`__
(which I love; I'm not a fan of GNOME 3).

- Whatever; I'm more happy with the built-in packages that come with
  Ubuntu 14.04 and that work well in MATE.

