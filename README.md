Login With Valid Credentials
    [Arguments]    ${email}    ${password}
    Input Text    ${LOGIN_EMAIL}       ${email}
    Input Text    ${LOGIN_PASSWORD}    ${password}
    Click Element    ${LOGIN_BUTTON}
    Wait Until Page Contains    Logged in as    10s
