# Skip Link Workaround
## Step 1: Add the following code to the header widget of the portal
**Client Script**
```
var element = $('<a>', {
		href: "javascript:void(0);",
		onclick: "$('h1[page-title]').attr('tabIndex', '-1').focus();return false;",
		"class": "sr-only custom-skip-link",
		text: $scope.data.customSkipToPageContent
	});
	$('body').prepend(element);
```

**Server Script**
```
data.customSkipToPageContent = gs.getMessage("Skip to page content")
```

## Step 2: Add the following styling to the CSS section of the portal record
```
.custom-skip-link {
    &:focus {
        background: $brand-primary;
        border-radius: 4px;
        color: white;
        display: inline-block;
        left: 3px;
        padding: 5px 10px;
        position: absolute;
        text-decoration: none;
        top: 3px;
        clip: auto;
        height: auto;
        width: auto;
        z-index: 9999;
    }
}
```


## Step 3: Test Functionality
After making the above changes, you should notice that upon opening a Service Portal page, you will not notice any changes. However, pressing the “tab” key will reveal a link in the upper-left-hand corner of the screen with the text “Skip to page content”. 

This link is only displayed when it has keyboard focus. Pressing the enter key will redirect the user’s focus to a hidden page title directly below the contents of the header. Resume tabbing and notice that the header has been skipped.

![](Skip%20Link%20Workaround/F5A58EA3-85A8-4314-89A3-641C72E3A070.png)

