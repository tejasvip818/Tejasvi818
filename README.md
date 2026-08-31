*** Settings ***
Library    RequestsLibrary
Library    Collections

*** Variables ***
${base_url}    https://api.open-meteo.com
${city}        Delhi

*** Test Cases ***
Get_weatherInfo
    Create Session    myssion    ${base_url}
    ${params}=    Create Dictionary
    ...    latitude=28.61
    ...    longitude=77.20
    ...    current_weather=true
    ${response}=    GET On Session    myssion    /v1/forecast    params=${params}

    Log To Console    ${response.status_code}

    ${json}=       Set Variable    ${response.json()}
    ${current}=    Set Variable    ${json['current_weather']}

    Log To Console    ${EMPTY}
    Log To Console    City: ${city}
    Log To Console    Temperature: ${current['temperature']} Degree celsius
    Log To Console    WindSpeed: ${current['windspeed']} Km per hour
    Log To Console    WindDirection: ${current['winddirection']} Degree
    Log To Console    Time: ${current['time']}
    Log To Console    Elevation: ${json['elevation']} meter
    Log To Console    Timezone: ${json['timezone']}
