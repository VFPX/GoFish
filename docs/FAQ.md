# GoFish FAQ

[What's New / Change Log](ChangeLog.md) 

[Report Issues / Ask Questions / Make Suggestions](https://github.com/VFPX/GoFish/issues)

<!-- <a href="#linkname">linkprompt</a>-->
<!-- <a id="linkname">linkprompt</a>-->
---

- <a href="#nodebugger">Why is GoFish so sloooow at times?</a>
- <a href="#columnsorting">How do I sort the columns in the grid?</a>
- <a href="#hiddenfeatures">Are there any "hidden" features?</a>
- <a href="#savechangesdialog">Why do I get the "Save Changes" dialog sometimes when I haven't changed anything?</a>
- <a href="#slowwildcardsearch">Why is wild card search sometimes so much slower than plain search?</a>
- <a href="#smartplainsearch">Is GF smart enough to use plain search if possible?</a>
- <a href="#twocommentchecks">Why are there two "Comment" checkboxes at the top of the screen? They seem to be in conflict with each other.</a>

---

### <a id="nodebugger">Why is GoFish so sloooow at times?</a>

GoFish can be ponderously slow if you have the debugger open.

Beyond that there is considerable variability depending on the scope of your search (i.e., the number of files searched) and whether you are using RegEx searching (which may take 3-5 times longer than plain or wildcard searches).

---

### <a id="columnsorting">How do I sort the columns in the grid?</a>

As you might expect, clicking on a column header causes sorting by that column.

However, there's a little more to it.  GF provides multi-level (or cascading) sorts:

- If you have sorted on column A and then sort on column B, column B becomes the primary sort, column A the secondary.  Then, sorting on column C makes C primary, B secondary, and A tertiary.  (There are a maximum of three levels.)

There are also sort-related options in the right-click context menu of column headers.

![](Screenshots/HeaderContextMenu.png)

---

### <a id="hiddenfeatures">Are there any "hidden" features?</a>

There are indeed features that are not visible as they are "hidden" either in context menus or described in tooltips.

Here are the places with context menus your should  be aware of:

- Right click on column header in the grid

![](Screenshots/gridheadercontextmenu.png)

- Right click on a cell in the grid

![](Screenshots/gridcellcontextmenu.png)

- Right click on a node in the treeview

![](Screenshots/treeviewrightclick.png)

In addition, there is one unexpected feature: if you right-click on the "Search" label at the upper left of the form, it will open up [Object Explorer](https://github.com/VFPX/ObjectExplorer) for the GF form.  

![](Screenshots/RightClickSearch.png)

---

### <a id="savechangesdialog">Why do I get the "Save Changes" dialog sometimes when I haven't changed anything?</a>
By default, if you double-click on a row in the grid to edit it and that row corresponds to a control contained in the form/class being edited, GF attempts to select that control (Issue #194).

In doing so, GF may change some properties and then reset them to their original values.  However, this causes VFP to think the form/class has been edited, so the "Save Changes" appears when closing the form/class.

You may disable this feature in the options screen:

![](Screenshots/GF_Options_SelectControl.png)

--- 

### <a id="slowwildcardsearch">Why is wild card search sometimes so much slower than plain search?</a>

WildCard search has a lot more to do because it looks for matches in the current statement (which may span continuation lines) rather than just the current line. Abstractly:
1. Find a plain match to whatever precedes the first '*' in the search phrase.
2. Determine the entire statement where the match is found.
3. Find a wildcard match to the entire statement.

---

### <a id="smartplainsearch">Is GF smart enough to use plain search if possible?</a>

Plain search and wildcard search are equally effective if no wildcard characters are used.  Thus the only time there is a reason to choose one over the other is if wildcard characters are used and you need to indicate whether they are treated as wildcard characters.

If you use RegEx searching and no wildcard characters are used, then GF uses plain search.

---

### <a ID="twocommentchecks">Why are there two "Comment" checkboxes at the top of the screen? They seem to be in conflict with each other.</a>

This is a historical artifact.

The top one (which has been around for a long time), which can be seen here:

![](Screenshots/Comments1.png)

is used during the search phase to exclude comment records from the results grid. If you later decide you actually do want to see the comments, you must re-run the search. (This has been kept for backward compatibility.)

The lower one (new in version 7) is used to filter the grid after the search. Selecting "Code Only" has the effect of filtering out comments.

![](Screenshots/Comments2.png)

The suggestion is to leave the top one always checked and use the lower one to filter out comments if desired.

---

[What's New](ChangeLog.md) 

[Report Issues / Ask Questions](https://github.com/VFPX/GoFish/issues)
