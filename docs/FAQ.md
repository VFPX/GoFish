# GoFish FAQ

- [Why do I get the "Save Changes" dialog sometimes when I haven't changed anything?](#why-save-changes-dialog-if-nothing-changed)
- [Why is wild card search sometimes so much slower than plain search?](#why-is-wildcard-search-slower)
- [Is GF smart enough to use plain search if possible ?](#plain-search-if-possible)

---

## Why Save Changes Dialog if Nothing Changed
By default, if you double-click on a row in the grid to edit it and that row corresponds to a control contained in the form/class being edited, GF attempts to select that control (Issue #194).

In doing so, GF may change some properties and then reset them to their original values.  However, this causes VFP to think the form/class has been edited, so the "Save Changes" appears when closing the form/class.

You may disable this feature in the options screen:

![](Screenshots/GF_Options_SelectControl.png)

## Why is WildCard Search Slower
WildCard search has a lot more to do because it looks for matches in the current statement (which may span continuation lines) rather than just the current line. Abstractly:
1. Find a plain match to whatever precedes the first '*' in the search phrase.
2. Determine the entire statement where the match is found.
3. Find a wildcard match to the entire statement.

## Plain Search if Possible
Plain search and wildcard search are equally effective if no wildcard characters are used.  Thus the only time there is a reason to choose one over the other is if wildcard characters are used and you need to indicate whether they are treaded as wildcard characters.

If you use RegEx searching and no wildcard characters are used, then GF uses plain search.

