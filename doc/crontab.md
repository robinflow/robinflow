## Indroduction
Crontab app can realize timing tasks.
The syntax of crontab app usage is the same as crontab syntax on linux system, supporting minute level.
You can you crontab app to do daily tasks or running tasks every Monday...


<iframe 
    width="1280" 
    height="720" 
    src="https://www.youtube.com/embed/Hz3ueh1O5Co"  frameborder="0" 
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
    </iframe>
## Parameter

<img src="https://public-pic-1251784084.cos.ap-guangzhou.myqcloud.com/image-20210313204406862.png" alt="image-20210313204406862" style="zoom:50%;" />

The first 5 fields indicate：
 > * minute：0-59
 > * hour：1-23
 > * date：1-31
 > * month：1-12
 > * weekday：0-6（0 means Sunday）

There are some other special symbols：
 > * *： Means any moment
 > * ,：　Means split, for example：0 2,4 * * *, means 2 o'clock and 4 o'clock execution
 > *  －：Means range, for example：1-5 * * *, means 1 o'clock to 5 o'clock
 > *  /n : Means execute every n units, for example: */2 * * *, means execute every 2 hour.

### Demos

| Expression        | Description   |
| --------   | -----  |
| */10 * * * *      | Execute every 10 minutes   |
|  43 21 * * *        |   Execute at 21:43   |
|  15 05 * * *        |    Execute at 05:15    |
| 0 17 * * *|Execute at 17:00|
| 0 17 * * 1 |Execute at 17:00 every Monday|
| 0,10 17 * * 0,2,3|Execute at 17:00 and 17:10 every Sunday and Tuesday|
| 0-10 17 1 * *|Execute every 1 minute from 17:00 to 17:10 on the first day of every month|
| 42 4 1 * *|Execute every 1st day at 4:42|
| 0 21 * * 1-6|Execute at 21:00 from Monday to Saturday|
| 0,10,20,30,40,50 * * * *|Execute every 10 minutes|
| */10 * * * * |Execute every 10 minutes|
| * 1 * * *|Execute every 1 minute from 1:00 to 1:59|
| 0 1 * * *|Execute at 1:00|
| 0 */1 * * *|Execute every 1 hour|
| 0 * * * *|Execute every 1 hour|
| 2 8-20/3 * * *|Execute at 8:02,11:02,14:02,17:02,20:02|
| 30 5 1,15 * *|Execute at 5:30 on 1st and 15th|
