Enter Login Email
    [Arguments]    ${email}
    Input Text    ${txt_loginEmail}    ${email}

Enter Login Password
    [Arguments]    ${password}
    Input Text    ${txt_loginPassword}    ${password}

Click Login Button
    Click Button    ${btn_login}
    Sleep    3s

Verify Login Successful
    Page Should Contain Element    ${lbl_loggedInAs}

Verify Login Failed
    Page Should Contain Element    ${lbl_loginError}
