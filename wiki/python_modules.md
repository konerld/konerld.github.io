# Modules

## Random

    import random

### random.choice()
Choose a random element from a non-empty sequence

Examples:

    random.choice([1, 2, 3, 4, 5])
    random.choice(['apple', 'car', 'ball'])

### random.randint(i, j)
Return random integer in range from i to j

    in:
    random.randint(1,10)

    out:
    7

## Datetime

    import datetime

    in:
    print(datetime.datetime(1961, 4, 12, 9, 7, 0))
    out;
    1961-04-12 09:07:00

    in:
    start_time = dt.datetime(1961, 4, 12, 9, 7, 0)
    landing_time = dt.datetime(1961, 4, 12, 10, 55, 0)
    print(landing_time - start_time)
    out:
    1:48:00

Get current time:

    datetime.datetime.now() # by your local PC time
    datetime.datetime.utcnow() # by UTC

Addition time:

    now = dt.datetime.utcnow()
    period = dt.timedelta(hours=3)
    
    moscow_moment = now + period

Fornating:

    %H - hours
    %M - minutes
    %S - seconds
    %U - week number




    the_time = dt.datetime(2019, 5, 10, 19, 45)
    print('Самолёт прибывает в', the_time.strftime('%H:%M'))
    print(the_time.strftime('Последний снег выпал в %U-ю неделю года.'))
    print(the_time.strftime('А первый снег пошёл в %U-ю неделю.'))

## urllib.parse
    
    s = 'что такое backend'
    encoded = urllib.parse.quote(s)  # зашифрованная строка
    decoded = urllib.parse.unquote(encoded)  # расшифрованная обратно строка

## requests
    import requests


### GET method

    requests.get(url,
                params=<dict or list_of_tuples>
                headers=<dict or list_of_tuples> )

### responce code

    In:
    requests.get('https://ya.ru/white')
    or
    requests.get('https://ya.ru/white').response.status_code
    Out:
    <Response [200]>

    In:
    print(response.text)
    Out:
    '<html><head><meta charset="utf-8"><title>Яндекс</title></head><body style="background: #ffffff;"><table height="100%" width="100%"><tr align="center"><td align="center" valign="middle"><form name="web" action="https://yandex.ru/search/" method="get"><input style="font-size:large; color: #000000; background: #ffffff; border:none" name="text" type="text" size="50" maxlength="160" autofocus></form><script>document.web.text.focus()</script></td></tr></table></body></html>'

    In:
    response = requests.get('http://wttr.in/?0T')
    print(response.text)
    Out:
    Weather report: Moscow, Russia
                   Overcast
          .--.     11..12 °C
       .-(    ).   ↘ 11 km/h
      (___.__)__)  10 km
                   0.0 mm


### get header

    In:
    requests.get('https://ya.ru/white').response.headers
    Out:
    < all content of headers >

    In:
    requests.get('https://ya.ru/white').response.headers["content-type"]
    Out:
    < print content type >

    In:
    requests.get('https://ya.ru/white').response.headers{headers["date"]} 
    Out:
    < response time >


### Response headers

    request_headers = {
                        'Accept-Language': 'ru'
                        }
