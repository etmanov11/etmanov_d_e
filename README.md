# etmanov_d_e
Устанавливаем утилиту WGET командой sudo yum install wget

![image](https://github.com/user-attachments/assets/8b4c434f-9e1a-4300-92c2-ca4200cc9a17)

Получаем ошибку. Чтобы ее решить переходим в браузер, вставляем ошибку в поисковую строку и переходим на Stackoverflow. Там находим решение данной проблемы.
Для решения проблемы нужно в командной строке ввести команду su root и ввести пароль

![image](https://github.com/user-attachments/assets/0b21be17-8449-4526-9637-752d4c16e244)

Далее нужно ввести команду vi /etc/sudoers

![image](https://github.com/user-attachments/assets/e7d958ec-e413-4aa7-93dc-bc3e156d912f)

В открывшемся файле нужно найти строку, которая начинается с root, затем скопировать эту строку и вставить ее на следующей строке, заменив root на имя пользователя

![image](https://github.com/user-attachments/assets/c5f869fc-aba5-4e40-ac94-d197b5d8abd2)

После этого нужно нажать Esc -> Shift + ж -> ввести wq! -> Enter. После этого ошибка будет решена! Проверить это можно повторным вводом команды sudo yum install wget

![image](https://github.com/user-attachments/assets/509a3deb-80d0-411d-b13f-1763c88bad72)
