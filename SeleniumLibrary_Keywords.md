# SeleniumLibrary — Complete Keyword Reference

```robot
*** Settings ***
Library    SeleniumLibrary
```

---

## 1. BROWSER

```robot
Open Browser                  ${url}    chrome
Open Browser                  ${url}    firefox
Open Browser                  ${url}    headlesschrome
Close Browser
Close All Browsers
Maximize Browser Window
Set Window Size               1920    1080
Go To                         ${url}
Go Back
Reload Page
Set Selenium Implicit Wait    5s
Set Selenium Timeout          10s
Set Selenium Speed            0.5s
```

---

## 2. CLICK

```robot
Click Element                 ${locator}
Click Button                  ${locator}
Click Link                    ${locator}
Click Image                   ${locator}
Double Click Element          ${locator}
Click Element At Coordinates  ${locator}    10    20
```

**Kab kya:** Button → `Click Button`, Link → `Click Link`, baaki sab → `Click Element`.
Confusion ho to `Click Element` — wo har jagah kaam karta hai.

---

## 3. INPUT / TEXTBOX

```robot
Input Text            ${locator}    Tejasvi
Input Password        ${locator}    Test@1234
Clear Element Text    ${locator}
Press Keys            ${locator}    ENTER
Press Keys            ${locator}    CTRL+a
Press Keys            ${locator}    TAB
Choose File           ${locator}    C:/path/file.pdf
```

---

## 4. DROPDOWN

```robot
Select From List By Label      ${locator}    India      # screen pe jo dikhta hai  ← BEST
Select From List By Value      ${locator}    IN         # HTML ka value attribute
Select From List By Index      ${locator}    3          # position  ← avoid karo
Unselect From List By Label    ${locator}    India

${selected}=    Get Selected List Label    ${locator}
@{options}=     Get List Items             ${locator}

List Selection Should Be       ${locator}    India
List Should Have No Selections ${locator}
```

---

## 5. CHECKBOX / RADIO

```robot
Select Checkbox                    ${locator}
Unselect Checkbox                  ${locator}
Checkbox Should Be Selected        ${locator}
Checkbox Should Not Be Selected    ${locator}

Select Radio Button                gender    male
Radio Button Should Be Set To      gender    male
```

---

## 6. WAIT (sabse zaroori — Sleep ki jagah use karo)

```robot
Wait Until Element Is Visible          ${locator}    10s
Wait Until Element Is Not Visible      ${locator}    10s
Wait Until Element Is Enabled          ${locator}    10s
Wait Until Element Contains            ${locator}    text    10s
Wait Until Page Contains               text          10s
Wait Until Page Contains Element       ${locator}    10s
Wait Until Page Does Not Contain       text          10s
Wait Until Location Contains           /login        10s
Wait Until Keyword Succeeds            3x    2s    Click Element    ${locator}
```

---

## 7. VERIFY — ELEMENT

```robot
Element Should Be Visible          ${locator}
Element Should Not Be Visible      ${locator}
Element Should Be Enabled          ${locator}
Element Should Be Disabled         ${locator}
Element Should Contain             ${locator}    partial text
Element Should Not Contain         ${locator}    text
Element Text Should Be             ${locator}    exact text
Element Text Should Not Be         ${locator}    text
Element Attribute Value Should Be  ${locator}    href    /login
Page Should Contain Element        ${locator}
Page Should Not Contain Element    ${locator}
```

---

## 8. VERIFY — PAGE

```robot
Page Should Contain            Logged in as
Page Should Not Contain        Error
Title Should Be                Automation Exercise
Location Should Be             https://www.automationexercise.com/login
Location Should Contain        /login
Page Should Contain Link       ${locator}
Page Should Contain Button     ${locator}
Page Should Contain Textfield  ${locator}
Page Should Contain Checkbox   ${locator}
Page Should Contain List       ${locator}
Page Should Contain Image      ${locator}
```

---

## 9. GET (value nikalna)

```robot
${text}=      Get Text                  ${locator}
${value}=     Get Value                 ${locator}
${attr}=      Get Element Attribute     ${locator}    href
${css}=       Get Element Size          ${locator}
${count}=     Get Element Count         ${locator}
${title}=     Get Title
${url}=       Get Location
${source}=    Get Source
@{elements}=  Get WebElements           ${locator}
${element}=   Get WebElement            ${locator}
```

---

## 10. MOUSE / KEYBOARD / SCROLL

```robot
Mouse Over                  ${locator}
Mouse Down                  ${locator}
Mouse Up                    ${locator}
Scroll Element Into View    ${locator}
Drag And Drop               ${source}    ${target}
Drag And Drop By Offset     ${locator}    100    50
Open Context Menu           ${locator}          # right-click
Simulate Event              ${locator}    click
```

---

## 11. JAVASCRIPT (jab normal click fail ho)

```robot
Execute JavaScript    window.scrollTo(0, 1000)
Execute JavaScript    document.querySelector('#btn').click()

${el}=    Get WebElement    ${locator}
Execute JavaScript    arguments[0].click()    ARGUMENTS    ${el}
```

---

## 12. ALERT / POPUP

```robot
Handle Alert                ACCEPT           # OK dabao
Handle Alert                DISMISS          # Cancel dabao
${text}=    Handle Alert    LEAVE            # sirf text padho
Alert Should Be Present     Are you sure?
Alert Should Not Be Present
Input Text Into Alert       my text
```

---

## 13. FRAME / IFRAME

```robot
Select Frame            ${locator}
Select Frame            id=myframe
Unselect Frame
Current Frame Should Contain    text
Frame Should Contain            ${locator}    text
```

---

## 14. WINDOW / TAB

```robot
Switch Window           NEW
Switch Window           MAIN
Switch Window           title=Page Title
${handles}=    Get Window Handles
${titles}=     Get Window Titles
Close Window
```

---

## 15. SCREENSHOT

```robot
Capture Page Screenshot
Capture Page Screenshot       ${OUTPUT_DIR}/error.png
Capture Element Screenshot    ${locator}
Set Screenshot Directory      ${OUTPUT_DIR}/screenshots
```

---

## 16. TABLE

```robot
Table Should Contain           ${table}    text
Table Cell Should Contain      ${table}    2    3    text
Table Row Should Contain       ${table}    2    text
Table Column Should Contain    ${table}    1    text
Table Header Should Contain    ${table}    Name
${cell}=    Get Table Cell     ${table}    2    3
```

---

## 17. COOKIES

```robot
${cookies}=    Get Cookies
${cookie}=     Get Cookie       sessionid
Add Cookie     name    value
Delete Cookie  name
Delete All Cookies
```

---

## LOCATOR PREFIX

```robot
id:username
name:email
class:btn-primary
xpath://input[@id='email']
css:input[data-qa='login-email']
link:Signup / Login
partial link:Signup
tag:button
```

`xpath:` aur `xpath=` dono chalte hain — ek hi style project bhar me rakho.

---

## TOP 12 — inhi se 90% kaam ho jayega

```robot
Open Browser
Maximize Browser Window
Click Element
Click Button
Input Text
Select From List By Label
Select Checkbox
Wait Until Element Is Visible
Page Should Contain Element
Element Text Should Be
Get Text
Close Browser
```

---

## POORI LIST DEKHNE KE LIYE

```bash
libdoc SeleniumLibrary show all
libdoc SeleniumLibrary list          # sirf naam
libdoc SeleniumLibrary SeleniumDoc.html    # HTML doc bana lo
```

PyCharm me keyword type karte waqt `Ctrl+Space` dabao — suggestions aa jayengi.

---

## SAMPLE — sab milakar

```robot
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${url}        https://www.automationexercise.com/
${browser}    chrome

*** Test Cases ***
LoginTest
    Open Browser    ${url}    ${browser}
    Maximize Browser Window

    Click Element    xpath://a[normalize-space()='Signup / Login']
    Wait Until Element Is Visible    xpath://input[@data-qa='login-email']    10s

    Input Text     xpath://input[@data-qa='login-email']       test@yopmail.com
    Input Text     xpath://input[@data-qa='login-password']    Test@1234
    Click Button   xpath://button[normalize-space()='Login']

    Wait Until Page Contains Element    xpath://a[contains(text(),'Logged in as')]    10s
    Page Should Contain    Logged in as

    ${name}=    Get Text    xpath://a[contains(text(),'Logged in as')]//b
    Log To Console    Logged in user: ${name}

    Capture Page Screenshot    ${OUTPUT_DIR}/login_success.png
    Close Browser
```
