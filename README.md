# test

import requests

il = requests.get(
    url = "https://hr-t.dqprism.com/account/login",
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36'
    }
)

c1 = il.cookies.get_dict()

form_data = {
    "mobile":"18******5",
    "password":"34*****************ba8"
}

i2 = requests.post(
    url = "https://hr-t.dqprism.com/api/employer/login",
    data=form_data,
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36'
    },
    cookies = c1
)
c2 = i2.cookies.get_dict()
c1.update(c2)
i3 = requests.get(
    url = "https://hr-t.dqprism.com/admin/analysis/application",
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36'
    },
    cookies = c1
)

print(i3.text)
