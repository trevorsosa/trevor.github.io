## How to read and store values in a query string - Javascript

Javascript method to read values contained in a query string

* `var getUrlParameter = function getUrlParameter(sParam) {
    var sPageURL = window.location.search.substring(1),
        sURLVariables = sPageURL.split('&'),
        sParameterName,
        i;
    for (i = 0; i < sURLVariables.length; i++) {
        sParameterName = sURLVariables[i].split('=');
        if (sParameterName[0] === sParam) {
            return sParameterName[1] === undefined ? true : decodeURIComponent(sParameterName[1]);
        }
    }
};` 

Calling the above method and storing the value in a local variable

* `var id = getUrlParameter('id');` 

Thank you

Trevor Ngogodo
