
# dwm

## Basic Concepts

tag

:   like workspace in other window manager, but more.
    Windows are grouped by tags.
    Each window can be tagged with one or multiple tags.
    Selecting certain tags displays all windows with these tags.

window

:   each window is a running application.

:   Each screen contains a small status bar which displays all available tags,
    the layout, the number of visible windows,
    the title of the focused window,
    and the text read from the root window name property,
    if the screen is focused.

:   A floating window is indicated with an empty square
    and a maximised floating window is indicated with a filled square before the
    windows title.

:   The selected tags are indicated with a different color.

:   The tags of the focused window are indicated with a filled square in the top
    left corner.

:   The tags which are applied to one or more windows are indicated with an empty
    square in the top left corner.

:   Which tags are window display, it's managed by tagmask.

layout

:   dwm preset layouts include:

    ```cpp
    static const Layout layouts[] = {
            /* symbol     arrange function */

            /* first entry is default, managed in a master and staking area */
            { "[]=",      tile },
            /* no layout function means floating behavior */
            { "><>",      NULL },
            /* all windows are maximiszed to the screen size */
            { "[M]",      monocle },
            { "|M|",      centeredmaster },
            { ">M>",      centeredfloatingmaster },
            { "[@]",      spiral },
            { "[\\]",     dwindle },
    };
    ```
rule

:   rules for creating app window.
    Base on app's class, instance(WM\_CLASS) and title(WM\_NAME) properties
    and the given tag and floating mode setting actions are performed.

## Custome shortcuts
