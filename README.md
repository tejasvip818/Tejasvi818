*** Settings ***
Documentation     MYNTRA (https://www.myntra.com) - hover on Profile icon -> read details -> click "See More".
...
...               LOCATORS ARE IN SELECTORSHUB FORMAT.
...               For every element the SelectorsHub panel gives 3 things, so all 3 are listed:
...                 Rel XPath  -> used as the actual variable (this is what SelectorsHub shows first)
...                 CSS        -> given as an alternative in the comment
...                 Abs XPath  -> given in the comment only (brittle, never use it in real scripts)
...               Verified live on 26-Aug-2026 against the real DOM.
...
...               GOTCHA: the profile flyout floats OVER the right column. If it is still open, a click
...               meant for "See More" lands on "Gift Cards" and navigates away. Move the mouse off first.
Library           SeleniumLibrary

Suite Setup       Open Myntra
Suite Teardown    Close All Browsers

*** Variables ***
${BROWSER}                  chrome
${HOME_URL}                 https://www.myntra.com/
${PDP_URL}                  https://www.myntra.com/tshirts/jockey/jockey-lightweight-microfiber-half-sleeve-active-wear-tshirt-with-breathable-mesh---mv16/30258581/buy

# =========================================================================
# HEADER - Profile icon (the HOVER target)
# =========================================================================
# CSS : div.desktop-userIconsContainer
# Abs : /html[1]/body[1]/div[1]/div[1]/div[1]/header[1]/div[2]/div[2]/div[1]/div[1]
${PROFILE_ICON}             xpath=//div[@class='desktop-userIconsContainer']

# CSS : span.myntraweb-sprite.desktop-iconUser.sprites-headerUser
# Abs : .../header[1]/div[2]/div[2]/div[1]/div[1]/span[1]
${PROFILE_ICON_IMG}         xpath=//span[@class='myntraweb-sprite desktop-iconUser sprites-headerUser']

# CSS : span.desktop-userTitle
${PROFILE_ICON_LABEL}       xpath=//span[normalize-space()='Profile']

# =========================================================================
# FLYOUT that opens on hover
# =========================================================================
# CSS : div.desktop-userActions
${PROFILE_FLYOUT}           xpath=//div[@class='desktop-userActions']

# CSS : div.desktop-userActionsContent
${FLYOUT_CONTENT}           xpath=//div[@class='desktop-userActionsContent']

# CSS : div.desktop-infoTitle
# Abs : .../div[1]/div[2]/div[2]/div[1]/div[1]
${FLYOUT_TITLE}             xpath=//div[@class='desktop-infoTitle']

# CSS : div.desktop-infoEmail
# Abs : .../div[1]/div[2]/div[2]/div[1]/div[2]
${FLYOUT_SUBTITLE}          xpath=//div[@class='desktop-infoEmail']

# CSS : a.desktop-linkButton
# Abs : .../div[1]/div[2]/div[2]/div[2]/div[1]/a[1]
${LOGIN_SIGNUP_BTN}         xpath=//a[@class='desktop-linkButton']

# ---- the 10 menu links (SelectorsHub Rel XPath for each) ----
# all of them together : css=div.desktop-userActions a.desktop-info
${FLYOUT_ALL_LINKS}         xpath=//div[@class='desktop-userActions']//a[@class='desktop-info']
${LINK_ORDERS}              xpath=//a[normalize-space()='Orders']
${LINK_WISHLIST}            xpath=//a[@class='desktop-info'][normalize-space()='Wishlist']
${LINK_GIFT_CARDS}          xpath=//a[@class='desktop-info'][normalize-space()='Gift Cards']
${LINK_CONTACT_US}          xpath=//a[@class='desktop-info'][normalize-space()='Contact Us']
${LINK_MYNTRA_INSIDER}      xpath=//a[@class='desktop-info'][contains(.,'Myntra Insider')]
${LINK_MYNTRA_CREDIT}       xpath=//a[@class='desktop-info'][normalize-space()='Myntra Credit']
${LINK_COUPONS}             xpath=//a[@class='desktop-info'][normalize-space()='Coupons']
${LINK_SAVED_CARDS}         xpath=//a[@class='desktop-info'][normalize-space()='Saved Cards']
${LINK_SAVED_VPA}           xpath=//a[@class='desktop-info'][normalize-space()='Saved VPA']
${LINK_SAVED_ADDRESSES}     xpath=//a[@class='desktop-info'][normalize-space()='Saved Addresses']

# =========================================================================
# PRODUCT PAGE - the "See More" step
# =========================================================================
# CSS : h1.pdp-title   | Abs : /html[1]/body[1]/div[2]/div[1]/div[1]/main[1]/div[2]/div[2]/div[1]/h1[1]
${PDP_BRAND}                xpath=//h1[@class='pdp-title']
# CSS : h1.pdp-name    | Abs : .../div[2]/div[2]/div[1]/h1[2]
${PDP_NAME}                 xpath=//h1[@class='pdp-name']
# CSS : span.pdp-price | Abs : .../div[1]/div[1]/p[1]/span[1]
${PDP_PRICE}                xpath=//span[@class='pdp-price']
# CSS : div.index-sizeFitDesc
${SPEC_SECTION}             xpath=//div[@class='index-sizeFitDesc']
# CSS : div.index-showMoreText | Abs : .../div[3]/div[1]/div[4]/div[2]
${SEE_MORE_LINK}            xpath=//div[@class='index-showMoreText']
# CSS : div.index-tableContainer
${SPEC_TABLE}               xpath=//div[@class='index-tableContainer']
${SPEC_ROWS}                xpath=//div[@class='index-tableContainer']//div[@class='index-row']
${SPEC_ROW_KEYS}            xpath=//div[@class='index-row']//div[@class='index-rowKey']
${SPEC_ROW_VALUES}          xpath=//div[@class='index-row']//div[@class='index-rowValue']

*** Test Cases ***
TC01 Hover On Profile Icon And Read Flyout Details
    [Documentation]    Step 1 + 2 : hover the Profile icon and assert everything inside the flyout.
    Go To                               ${HOME_URL}
    Wait Until Element Is Visible       ${PROFILE_ICON}         timeout=30s
    Element Text Should Be              ${PROFILE_ICON_LABEL}   Profile

    Mouse Over                          ${PROFILE_ICON}
    Wait Until Element Is Visible       ${FLYOUT_CONTENT}       timeout=10s

    Element Text Should Be              ${FLYOUT_TITLE}         Welcome
    Element Text Should Be              ${FLYOUT_SUBTITLE}      To access account and manage orders
    Element Text Should Be              ${LOGIN_SIGNUP_BTN}     LOGIN / SIGNUP

    Element Should Be Visible           ${LINK_ORDERS}
    Element Should Be Visible           ${LINK_WISHLIST}
    Element Should Be Visible           ${LINK_GIFT_CARDS}
    Element Should Be Visible           ${LINK_CONTACT_US}
    Element Should Be Visible           ${LINK_SAVED_ADDRESSES}

    ${links}=    Get WebElements        ${FLYOUT_ALL_LINKS}
    Length Should Be                    ${links}                10
    FOR    ${l}    IN    @{links}
        Log    Flyout link -> ${l.text}
    END
    Move Mouse Away From Profile Icon

TC02 Click See More And Verify Specifications Expand
    [Documentation]    Step 3 : the site's real "See More" (product specifications expander).
    Go To                               ${PDP_URL}
    Wait Until Element Is Visible       ${PDP_BRAND}            timeout=30s

    Move Mouse Away From Profile Icon       # flyout must NOT overlap the right column
    Scroll Element Into View            ${SEE_MORE_LINK}
    ${before}=    Get Element Count     ${SPEC_ROWS}

    Click Element                       ${SEE_MORE_LINK}
    Wait Until Keyword Succeeds    10x    1s    Spec Rows Should Be More Than    ${before}
    Element Should Not Be Visible       ${SEE_MORE_LINK}        # link vanishes once expanded

*** Keywords ***
Open Myntra
    Open Browser                        ${HOME_URL}     ${BROWSER}
    Maximize Browser Window             # Myntra header is desktop-only, needs a wide window
    Set Selenium Implicit Wait          5s

Move Mouse Away From Profile Icon
    Mouse Over                          xpath=//body

Spec Rows Should Be More Than
    [Arguments]    ${before}
    ${now}=    Get Element Count        ${SPEC_ROWS}
    Should Be True                      ${now} > ${before}
