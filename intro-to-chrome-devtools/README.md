
# Intro to Chrome Developer Tools

### Demo and example sites
- [NCTU - GMBA](http://gmba.nctu.edu.tw/main.php)
- [OODATA](http://61.216.30.33:10280/)
- [konekoya](http://konekoya.github.io/)
- [Date Generator](http://konekoya.github.io/date-generator/)
- [Buchbinderei](http://buchbinderei.it/)

## A brief History of Browser devTools
- View source(cmd + opt + u) is all you got, it's like a snapshot not the real DOM.
- Alert is not that helpful.
- Console.log everywhere.
- Firebug is the [game changer](http://getfirebug.com) back then.
- Modern bowsers all ship with devTools now!
- Try Chrome Canary.

## Editing and inspecting
Do remember to checkout to the right git branch
#### Elements panel
- Toggle devTools:
    - `cmd + opt + i` or F12.
    - `cmd + opt + c` open to inspect.
    - Right click on the el that you want to open with and select inspect
- Change devTools dock location:
    - click on the three dots and Dock side
- Some basic settings:
    - disable the cache
    - disable JavaScript
    - Change theme
- Panels, tools quick walk thru ->
    - elements
    - Console
    - Network
    - Application
    - Performance
    - Memory
    - Security
    - Audits
    - Animation
    - Rendering
    - Coverage
- Rearrange panel with mouse drag

- DOM tree
    - remember everything is in memory, when refreshing, every change will be gone.
    - expand and collpase the DOM tree with arrow keys(up, right down and left)
    - hit return key to edit the prop values or double click on the el
    - add, edit attr and edit HTML
    - delete els with delete key and ctrl + z for undo
    - drop and drap els.
    - inspect els with inspect tool
    - scroll into view
    - `$0` - `$4` in the console, `$0` as current selected el, and up to five($0 - $4) els in the history.

- Style panel
    - toggle to enable and disable rules.
    - click to edit props and values.
    - Crossed styles are the styles that were trumped by other styles.
    - click the source on the right to open the stylesheet in source panel.
    - use "+" icon to add new css selector.
    - add ".cls" to add new classes.
    - use ":hov" to toggle different states of the els.
    - inline styles with element style.
    - use color palettes and color picker to pick new colors.
    - shift + click to change color mode.
    - Color scheme with the color palettes.
    - filtering props via filter.
    - box model in the computed pane
    - actually applied styles in the computed pane
    - show all to see all the available props and user agent stylesheet

- Console panel
    - it's just like a JavaScript REPL (Read Evaluate, Print, Loop)
    - open and close with ESC key
    - inspect error and its source code
    - copy
    - pretty print
    - clear console
    - preserve log
    - CLI like history
    - `$('el')`
    - debug JS with logs

- Device Toolbar
    - Toggle device toolbar
    - throttling - be very careful with this option
    - change devices
    - testing with the real device

## Aduiting
#### Network panel
- Overview
    - toggle overview
    - expain waterfull / timing color meaning
    - clear and record
    - disable cache
    - throttling
    - filter
    - Load time

- Table
    - sort with table head
    - eable and disable table head
    - name, error with red color
    - Method
    - status - HTTP status code like 200, 40, 304
    - type
    - initiator
    - size - total size and content
    - priority

- Headers
    - General - summary
        - Request URL
        - Request Method
        - Status Code
    - Response
    - Request
    - Query String Parameters
- Preview
- Response
- Timing
    - Queued
    - Wainting(Time to First Byte) -- slow server, bad network conditions

- Capture screenshots

#### Audits panel
- Reload page and audit on load

## Debugging
#### Source panel
- Open file with `cmd + p` for fuzzy search
- Browser breakpoint(clicking the line number)
    - the code should be excuted not only exist
    - hover to inspect vars.
    - console has the current scope
    - deactivate breakpoints, Pause on exceptions
- Step through debugging
    - Resume script execution
    - Step over next function call
    - step into next function call
- Watch - for loop
- Call Stack
- Scope
- Debugger api, remove it when shipping
- Event Listener Breakpoints
- DOM Breakpoints

- Live editing - It’s like a live editor
    - setting up:
        1. Load the source folder and allow the permisson for chrome to access your file system.
        2. Link and sync the folder.
        3. Start editing.


## Real world use cases
- Checkout to the devTools-bugs
- Style panel
    - Example A: Change the submit btn background color to `#ff4444` and the text color to `#fff`
    - Example B: Fix the font family not applying on h2 issue
    - Example C: Remove one pixel border in result container
    - *Example D: Remove user agent margin from body

- Debugging network
    - Example E: Fix 404 status code and undefined name bug
    - Example F: Fix copied message not remove after the user click the body
