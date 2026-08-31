*** Settings ***
Library    RequestsLibrary
Library    Collections

*** Variables ***
${base_url}    https://api.open-meteo.com

*** Test Cases ***
Get_weatherInfo
    Create Session    myssion    ${base_url}
    ${params}=    Create Dictionary    latitude=28.61    longitude=77.20    current_weather=true
    ${response}=    GET On Session    myssion    /v1/forecast    params=${params}

    # VALIDATIONS
    ${status_code}=    Convert To String    ${response.status_code}
    Should Be Equal    ${status_code}    200

    ${body}=    Convert To String    ${response.content}
    Should Contain    ${body}    temperature
