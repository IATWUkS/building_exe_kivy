# building_exe_kivy
Изначально устанавливаем python последней версии с официального сайта (python.org). При установки добавляем в PATH.

**Устанавливаем нужные модули:
**
setuptools
wheel
kivy
pyinstaller
pycrypto


# Изменения некоторых файлов в site_packages
1. Перейдите по пути C:\Users\имя_компьютера\AppData\Local\Programs\Python\Python39\Lib\site-packages\kivy\deps

2. **Откройте файл __unit__.py редактором и добавте следующие строки:**
import sdl2
import glew

**После установите модуль tinyaes:**
pip install tinyaes
## Важно, для установки модулей нужен Windows 10 SDK build tools


# Компиляция
В папке с проектом создайте папку src и перенесите все файлы проекта в неё.
Дальше вам нужно скачать spec файл: https://drive.google.com/file/d/11m9A_9qVl2Dpdv5sXpkFDECTaYrVMwJA/view?usp=sharing.

Как это будет выглядеть:
![image](https://user-images.githubusercontent.com/63918733/132127147-18f262f0-bce3-4865-a8c2-c2c708037b93.png)

**В самом spec файлы нужно изменить следующие строки:
**
Названия приложения: app_name = 'rbplay'
         
Путь к папке с проектом: pathex=['C:\\Users\\имя_компьютера\\Desktop\\rbplay-master']

_Важно, указывать путь нужно не к src папке, а к начальной, где находится сама папка src._

После открываем консоль и в ней переходим в нашу папку с spec файлом/

**Пример:
**
cd C:\\Users\\имя_компьютера\\Desktop\\rbplay-master

Вводим команду:
python -m PyInstaller single.spec

После ждем компиляции всего проекта, exe появится в папке dist.


# Создание установщика

Если в проекте есть json, txt и прочие файлы, с которыми программа взаимодействует, кроме .py, то переместите .exe из dist в папку с этими файлами. Пример:

![image](https://user-images.githubusercontent.com/63918733/132245915-222c538a-2034-4148-b697-3fab7d189e03.png)
![image](https://user-images.githubusercontent.com/63918733/132245925-74815364-83fa-41fd-a503-b51b25778c65.png)
![image](https://user-images.githubusercontent.com/63918733/132245935-cb0a96c3-a80d-4f88-b473-556c98e659d8.png)

Удобнее всего будет создать новую папку и скопировать сам .exe и json файлы.
Важно сохранить структуру проекта, которая была до этого.

## Создание sfx архива
Нужен WinRar.

Правой кнопкой мыши по папке, куда вы перекинули .exe и json.

![image](https://user-images.githubusercontent.com/63918733/132247769-bd4431b6-4f8e-46ea-90cf-1091a26c825a.png)

После:

![image](https://user-images.githubusercontent.com/63918733/132247810-090693ed-25fe-4d3d-872e-fafe83131ed0.png)

Дальше:

![image](https://user-images.githubusercontent.com/63918733/132247906-aff74286-a8ff-4be4-a062-188f9c79ee90.png)

Переходим вкладку:

![image](https://user-images.githubusercontent.com/63918733/132247870-97318eb6-7c25-48a1-86be-0230db9eac83.png)

Нажимаем на кнопку:

![image](https://user-images.githubusercontent.com/63918733/132247920-953c2ef4-7eed-4b42-a7cf-d1a55461ff78.png)

Вводим путь:

![image](https://user-images.githubusercontent.com/63918733/132247967-97053511-dff1-4393-aae1-ff1912425978.png)

На этом все.
