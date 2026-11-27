    # dropdown kholo
    SeleniumLibrary.Wait Until Element Is Visible    //span[contains(@id,'ProcessType-arrow')]    timeout=30s
    SeleniumLibrary.Click Element                    //span[contains(@id,'ProcessType-arrow')]
    Sleep    2

    # option click karo
    SeleniumLibrary.Wait Until Element Is Visible    //li[contains(normalize-space(.),'EAM : Consolidation for FL tasklist')]    timeout=20s
    SeleniumLibrary.Click Element                    //li[contains(normalize-space(.),'EAM : Consolidation for FL tasklist')]
    Sleep    2
