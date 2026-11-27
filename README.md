    # Process Goal dropdown kholo
    SeleniumLibrary.Wait Until Element Is Visible    //span[contains(@id,'GoalCB-arrow')]    timeout=30s
    SeleniumLibrary.Click Element                    //span[contains(@id,'GoalCB-arrow')]
    Sleep    2

    # "Consolidation of Source Records" click karo
    SeleniumLibrary.Wait Until Element Is Visible    //li[normalize-space(text())='Consolidation of Source Records']    timeout=20s
    SeleniumLibrary.Click Element                    //li[normalize-space(text())='Consolidation of Source Records']
    Sleep    2
