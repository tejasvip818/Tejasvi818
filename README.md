    # Adapt Filters kholo
    SeleniumLibrary.Wait Until Element Is Visible    //button[contains(@id,'ssbSmartFilter-btnFilters')]    timeout=30s
    SeleniumLibrary.Click Element                    //button[contains(@id,'ssbSmartFilter-btnFilters')]
    Sleep    3

    # Supplier search karo
    SeleniumLibrary.Input Text    //div[contains(@class,'sapMDialog')]//input[@placeholder='Search for Filters']    Supplier
    Sleep    2

    # checkbox tick karo
    SeleniumLibrary.Click Element    //tr[.//*[normalize-space(text())='Supplier']]//div[contains(@class,'sapMCbBg')]
    Sleep    2

    # OK
    SeleniumLibrary.Click Element    //button[contains(@id,'adapt-filters-dialog-confirmBtn')]
    Sleep    3

    # ab Supplier field aa gaya — value daalo
    SeleniumLibrary.Wait Until Element Is Visible    //input[contains(@id,'-Supplier-inner')]    timeout=30s
    SeleniumLibrary.Input Text                       //input[contains(@id,'-Supplier-inner')]    69009855
    SeleniumLibrary.Press Keys                       //input[contains(@id,'-Supplier-inner')]    ENTER
    Sleep    2

    # Go
    SeleniumLibrary.Click Element    //button[contains(@id,'ssbSmartFilter-btnGo')]
    Sleep    5
    SeleniumLibrary.Take Screenshot
