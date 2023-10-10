---
layout: post
title: "Email Generator | تولید کننده ایمیل"
author: "ALIILAPRO"
categories: journal
tags: [learn,sample,python,code,email]
image: email.jpg
---

<div dir="rtl" style="white-space: pre-line; markdown="1">

خب بعضی ها تون یدونه ایمیل دارید یا کلا چند تا دارید یا بازم اینکه از یدونه ایمیل استفاده می کنید برای ثبت نام

خب اینطوری اگر تو یه سایت ثبت نام کنید به هر دلیلی بخواید تو همون سایت دوباره ثبت نام کنید باید برید سراغ ایمیل دیگه یا این که فیک میل 

خب ایمیل دیگه که باهاش کاری نداریم میمونه فیک میل که اونم دردسر های خودش رو داره راحت ترینش اینکه ممکنه دیگه بهش دسترسی نداشته باشید خیلی راحت 🤷🏻‍♂

خب میایم از ترفند «.» یا «+» استفاده می کنیم ( من gmail , protonmail رو تست کردم اوکی بود )

به این شکل که dot یا plus رو به یوزرنیم ایمیل اضافه می کنید در کل ظاهر ایمیل عوض میشه و شبیه قبلی نیست اما بازم همون ایمیل و اینکه اگر جایی باهاش ثبت نام کنید برای همون صندوق ایمیل قبلی پیام ها میاد و نیازی نیست نه سراغ سایت های فیک میل برید یا ایمیل جدید بسازید 
رو سایت های ایرانی کلا اوکیه و راحت میشه استفاده کرد😂

رو خارجی ها هم کم و بیش اجازه استفاده از این رو روش رو میدن

این چیز جدیدی نیست که بخوام بگم کشفش کردم و اینا 😂 نه گفتم بگم بهتون چون میدونم نیازه

یدونه کد پایتون هم زدم براش کمی تایم خدمت اجازه بده بهترش میکنم ( چراااا خدمت چون پست مال اون موقع هستش الا دیگه تموم شده:/ )
</div>


```python
cash_db = []

def generator(Username, num, model):
    global cash_db
    temp = ''
    for i in range(num, len(Username)):
        temp = Username[:i] + f'{model}' + Username[i:]
        if temp not in cash_db:
            if f'{model}{model}' not in temp:
                cash_db.append(temp)
                generator(temp, num+2, model)
    return cash_db

email_addres = input('[#] Enter the Email address: ')
type_gn = input('[#] DOT (.) = 1  plus (+) = 2: ')
if '@' in email_addres:
    username = email_addres.split('@')[0]
    domain = email_addres.split('@')[1]
username = username.replace('.','')
if type_gn == '1':
    model = '.'
elif type_gn == '2':
    model = '+'
generator(username, 1, model)
file = open(f'fake-e[{username}-by{model}-{domain}].txt', 'w')
for i in cash_db:
    temp = str(i) + f'@{domain}'
    file.write(temp)
    file.write("\n")
print('Done.')
```
