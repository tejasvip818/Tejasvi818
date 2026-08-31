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
    Log To Console    ${response.status_code}
    Log To Console    ${response.content}
