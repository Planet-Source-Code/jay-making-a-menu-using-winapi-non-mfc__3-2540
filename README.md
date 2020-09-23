<div align="center">

## Making a menu using winapi non\-mfc


</div>

### Description

This code shows how to easily and quickly create a menu on a non-mfc window using winapi. I this code is versatile, and extremely useful as I for one hate resources. This example deals with making a "file --> exit" menu. The methods used in making this apply to all menus.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Jay](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jay.md)
**Level**          |Beginner
**User Rating**    |5.0 (40 globes from 8 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__3-3.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jay-making-a-menu-using-winapi-non-mfc__3-2540/archive/master.zip)





### Source Code

```
//define any menu ITEMS u might have, in this case "exit"
#define CM_MENU_FILE_EXIT 2001
//place this in LRESULT CALLBACK WindowFunc
HMENU hMenu, hSubMenu;
//create the menu in the WM_CREATE section of LRESULT CALLBACK WindowFunc
hMenu = CreateMenu();
hSubMenu = CreatePopupMenu();
AppendMenu(hSubMenu, MF_STRING, CM_MENU_FILE_EXIT, "E&xit");
AppendMenu(hMenu, MF_STRING | MF_POPUP, (UINT)hSubMenu, "&File");
SetMenu(hwnd, hMenu);
//note - if creating extra menus dont forget to call hSubmenu = CreatePopupMenu(); again or all your "menu items" will just b added to the old menu
//give the "menu item" an action under WM_COMMAND
switch(LOWORD(wParam)) {
case CM_MENU_FILE_EXIT:
PostMessage(hwnd, WM_CLOSE, 0, 0);
break;
}
//i hope this has been helpful, feel free to comment
```

