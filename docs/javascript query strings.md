## How to read and store values in a query string - Javascript

Javascript method to read values contained in a query string

* function UrlVal(Value) {
    var WebPage = window.location.search.substring(1),
        PageVar = WebPage.split('&'),
        VarName,
        i;
    for (i = 0; i < PageVar.length; i++) {
        VarName = PageVar[i].split('=');
        if (VarName[0] === Value) {
            return VarName[1] === undefined ? true : decodeURIComponent(VarName[1]);
        }
    }
};` 

Calling the above method and storing the value in a local variable

* `var id = UrlVar('id');` 

Thank you

Trevor Ngogodo
