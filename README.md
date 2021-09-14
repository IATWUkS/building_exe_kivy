# building_exe_kivy
Рекомендуемая версия python3.6, для запуска программы на Windows 7

Нужные модули:

setuptools

wheel

kivy

pyinstaller

pycrypto
# Изменения некоторых файлов в site_packages
Перейдите по пути C:\Users\имя_компьютера\AppData\Local\Programs\Python\Python39\Lib\site-packages\kivy\deps

Откройте файл __unit__.py редактором и добавте следующие строки:

import sdl2
import glew

После установите модуль tinyaes

pip install tinyaes
## Важно, для установки модулей нужен Windows 10 SDK build tools

# Компиляция
В папке с проектом создайте папку src и перенесите все файлы проекта в неё.
Дальше вам нужно скачать spec файл: https://drive.google.com/file/d/15yt15IZPLcq5A61meWWFVkkX1mMAIwzP/view?usp=sharing

Как это будет выглядеть:

![image](https://user-images.githubusercontent.com/63918733/132127147-18f262f0-bce3-4865-a8c2-c2c708037b93.png)


В самом spec файлы нужно изменить следующие строки:

Названия приложения

app_name = 'rbplay'
         
Путь к папке с проектом

pathex=['C:\\Users\\имя_компьютера\\Desktop\\rbplay-master']

Важно, указывать путь нужно не к src папке, а к начальной, где находится сама папка src

После открываем консоль и в ней переходим в нашу папку с spec файлом

Пример:

cd C:\\Users\\имя_компьютера\\Desktop\\rbplay-master

Вводим команду

python -m PyInstaller single.spec

После ждем компиляции всего проекта, exe появится в папке dist

# Создание установщика

Если в проекте есть json, txt и прочие файлы, с которыми программа взаимодействует, кроме .py, то переместите .exe из dist в папку с этими файлами. Пример:

![image](https://user-images.githubusercontent.com/63918733/132245915-222c538a-2034-4148-b697-3fab7d189e03.png)
![image](https://user-images.githubusercontent.com/63918733/132245925-74815364-83fa-41fd-a503-b51b25778c65.png)
![image](https://user-images.githubusercontent.com/63918733/132245935-cb0a96c3-a80d-4f88-b473-556c98e659d8.png)

Удобнее всего будет создать новую папку и скопировать сам .exe и json файлы.
Важно сохранить структуру проекта, которая была до этого.

## Создание установщика.
Скачиваем программу Smart Install Maker

http://ru.sminstall.com/

Ключ активации: name: phpbb3 serial: Q8ZZZ-MV417-E0P2T-3MA3L-N24UV

Переходим в вкладку General

![image](https://user-images.githubusercontent.com/63918733/133259236-bab2b0ad-66c2-49b3-bbb7-f025bef16054.png)


Product name - Название программы, больше тут ничего не нужно.

В Save as можно указать путь, где будет лежать установщик.

Переходим во вкладку Files, на + добавляем папку с файлами. Скрины:

![image](https://user-images.githubusercontent.com/63918733/133259831-601d0305-b844-4f48-83ae-c85219226617.png)

Выбираем папку с файлами и жмем ок.

![image](https://user-images.githubusercontent.com/63918733/133260038-fba44e8c-325a-4ca2-bd04-efa8eae70541.png)

По итогу выйдет:

![image](https://user-images.githubusercontent.com/63918733/133260163-314243d0-eaa0-4513-be4b-c1f986b038de.png)

В Dialogs найдите Destination path и измените его по примеру:

![image](https://user-images.githubusercontent.com/63918733/133260476-a4210a6f-f5be-4e89-809e-41117d153d1d.png)

Чтоб автоматически создавался ярлык зайдите в shortcuts, нажми на кнопку add и заполните по примеру:

![image](https://user-images.githubusercontent.com/63918733/133260761-57b42cfa-2627-47ed-81f0-21a3d05d59b7.png)

Чтоб автоматически запускать установку доп.программ, зайдите в Commands, дальше нажмите кнопку add(+) и заполните по примеру:

![image](https://user-images.githubusercontent.com/63918733/133261022-d423e6cc-ce4c-450a-82c1-5b17faa848d1.png)

Где после %InstallPath%\ введите названия программы, которая должна установиться.

После нажмите 

![image](https://user-images.githubusercontent.com/63918733/133261587-78032744-d5e8-4950-8388-2fbe31bade0a.png)

Начнется сборка установщика, он появится в папке Documents

На этом все.
