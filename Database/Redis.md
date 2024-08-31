
open the Redis terminal with redis-cli

SET command to add new record to Redis
SETEX to add with expiration time

```sql
setex azadeh 60 darabi
```

GET command to get the value of the key from db

DEL command to delete it

EXISTS command to check if the key value is in database

TTL to check the time to live of the data

EXPIRE to set expiration time for data:

```sql
EXPIRE user1 60
```

to run Redis commands from .txt file:

```bash
cat Command.txt | redis-cli
```
or

```bash
docker exec -i redis-stack-server redis-cli < Command.txt
```

to get all keys:

```sql
KEYS <pattern>
```
or

```sql
SCAN <cursor> MATCH <pattern>
```
match can be empty, cursor is an integer to say from where start to scan

```sql
SCAN 0
```

```sql
SCAN 0 MATCH user*
```

## فضای نام (Namespaceها)

فرض کنید که قصد دارید چهار کاربر مختلف را در دیتابیس خود مدیریت کنید.

هر کدام از این چهار کاربر، خصیصه‌هایی مثل _username_ و _password_ دارند. چه ساختار نام‌گذاری برای کلید‌ها در این فضا پیشنهاد می‌دهید؟

یکی از راه‌های مدیریت این داده‌ها این است که هر کدام را جداگانه نام‌گذاری کنیم. به دستورات زیر دقت کنید:


```sql
127.0.0.1:6379> SET user1Username matin
127.0.0.1:6379> SET user2Username moein
127.0.0.1:6379> SET user3Username youness
127.0.0.1:6379> SET user4Username ali
```


در این حالت، هر کدام از کلید‌ها، نام خاص خود را دارند و این کار را برای نوشتن‌ کوئری‌های مختلف سخت می‌کند. شما در این حالت هیچ راه ساده‌ای برای دریافت تمام _username‌_ ها ندارید و نیاز است تا راه ساده‌تری برای نام‌گذاری‌ها ایجاد کنیم.

پیشنهاد ردیس برای این فضا، _namespace‌_ ها هستند. _namespace‌_ ها یک نام به عنوان _prefix_ به هر کلید اضافه می‌کند که امکان مدیریت بهتری را در این فضا ایجاد می‌کند. در این حالت شما امکان نوشتن کوئری‌های مختلفی را خواهید داشت که می‌توان کار را برای شما بسیار ساده کند. برای استفاده از _namespace‌_ ها می‌توانید دستورات بالا را به شکل زیر تغییر دهید:


```sql
SET user:1:username matin
SET user:2:username moein
SET user:3:username youness
SET user:4:username ali
```


ما در اینجا از دو _namespace_ به صورت همزمان استفاده کرده‌ایم. اول، گفته‌ایم که تمام این داده‌ها مرتبط با کلید _user_ هستند. بعد از آن یک _identifier_ اضافه کرده‌ایم که باعث ایجاد تفاوت در داده‌ها شود و در نهایت از صفات کاربر ویژگی _username_ مقدار اصلی است که در حال مقداردهی آن هستیم. پیاده سازی داده‌ها به این شکل ساختارمندتر و درک آنها راحت‌تر است و این مدل، شکل مرسوم و شناخته شده آن است.

در نهایت با استفاده از دستور `KEYS` می‌توانیم به تمام داده‌ها دسترسی داشته باشیم. برای مثال با دستور زیر ما لیستی از تمام الگو‌های _username‌_ دریافت خواهیم کرد:


```sql
keys user:*:username
```

حال دستور بالا را به فرم اسکن به شکل زیر است:


```sql
SCAN 0 MATCH user:*:username
```

درواقع دستورات بالا میگویند دنبال کلید‌هایی بگرد که شروع آن با `user:` و وسط دستور میتواند هرچیزی باشد (باتوجه به این که از ستاره استفاده کرده‌ایم) و انتهایش به شکل `:username` ختم شود.

خروجی این دستور در فضای _redis-cli_ به شکل زیر خواهد بود:


```sql
1) "user:1:username"
2) "user:2:username"
3) "user:4:username"
4) "user:3:username"
```
