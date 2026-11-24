
    SeleniumLibrary.Click Element    ${DisplayCurrency_Field}
    SeleniumLibrary.Press Keys       ${DisplayCurrency_Field}    CTRL+a
    SeleniumLibrary.Press Keys       ${DisplayCurrency_Field}    DELETE
    Sleep    1s
    
    SeleniumLibrary.Input Text       ${DisplayCurrency_Field}    aud
    Sleep    2s


    SeleniumLibrary.Wait Until Element Is Visible    ${AUD_Suggestion}    timeout=20s
    SeleniumLibrary.Click Element                    ${AUD_Suggestion}
    Sleep    2s


    ${value}=    SeleniumLibrary.Get Value    ${DisplayCurrency_Field}
    Should Contain    ${value}    AUD
    Log    Display Currency set to: ${value}


    SeleniumLibrary.Click Element    ${Go_Button}
    Sleep    5s
    SeleniumLibrary.Take Screenshot
