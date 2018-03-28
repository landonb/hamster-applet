############################
Hamster Time Tracking Applet
############################

A tweak of the Hamster `GNOME <https://www.gnome.org/>`__ applet.

1. Opening the Overview dialog shows the daily summary, rather than the weekly summary.

  - Thus you can see the current day's activities without having to scroll.

2. The Totals screen shows two decimal places for each Activity, rather than just one decimal place.

  - A tenth of an hour is a full 6 minutes, but a hundredth of an hour is just 36 seconds.

    - If you're tracking project time on a ticket-by-ticket basic, using more precision
      makes your task accounting more accurate, especially if you switch between the
      same handful of tasks multiple times per day.

  - Select one of more Categories to see two decimal places; if no categories are
    selected, the display still just shows one decimal place.

Using this fork
---------------

Install hamster 2.9 packages from Ubuntu and replace a few files.

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

- The Overview dialog is less useful in 3.x — it only shows weekly activity,
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

