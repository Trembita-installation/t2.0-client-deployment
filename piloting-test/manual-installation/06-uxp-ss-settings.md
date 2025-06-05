Відкриваєм вебінтерфейс шлюзу безпечного обміну
https://\<Your-security-server-IP\>:4000

<hr />

Якщо скриптом встановлювалося, при першому вході.
![](image45.png)

<hr />
Якщо (ручна інсталяція)
То виконуємо наступні кроки.

<hr />

1. Завантажити **ліцензію для шлюзу безпечного обміну**.
   ***member.live.license.lic***
   Це перший крок після першого входу.  
   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/zavantazennya-licenziyi-dlya-slyuzu-bezpecnogo-obminu>

<hr />

2. Завантажити **файл якоря конфігурації**
   configuration_anchor_SEVDEIR-TEST.xml
   ![](image46.png){width=70%}
   Потім
   ![](image47.png){width=70%}
   Натискаємо "**підтвердити**"
   Наступне вікно заповнюємо
   ![](image41.png)

   Заповнюємо
   ![](image.png)
   Код сервера безпеки: <span style="color:red;">Замінити uxpadmin</span>
   PIN - тільки цифри
   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/inicializaciya-slyuzu-bezpecnogo-obminu>

<hr />

3. Введення PIN-коду програмного токену
   Після ініціалізації з’явиться помаранчеве повідомлення у верхній частині сторінки з написом «Будь ласка, введіть PIN-код програмного токену».
   ![](image42.png){width=70%}

   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/vvedennya-pin-kodu-programnogo-tokenu>

<hr />

4. Налаштування сервера позначок часу
   ![](image50.png){width=70%}
   Додаємо

   ![](image51.png){width=70%}
   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/nalastuvannya-servera-poznacok-casu>

<hr />

5. Імпорт ключа підпису та шифрування

<details class="details-info-box_green details-notice details-notice__hint" style="border-left:3px solid #00ff00; background-color:#f2f5f7; padding:5px;"><summary>на тестовому середовищі</summary><summary></summary>
<p>Якщо налаштування виконуються на <strong>тестовому майданчику </strong>(для тестового шлюзу безпечного обміну) і використовується <strong>програмний (файловий) контейнер </strong>для зберігання особистих ключів електронної печатки та шифрування.</p>
<p>Їх необхідно підготувати для імпорту на шлюз (запакувати в ZIP-архів):<br />
Зазначені файли повинні мати лише латинські літери та цифри у найменуванні.</p>
<ul>
	<li>файл особистого ключа (зазвичай, це Key-6.dat)</li>
	<li>сертифікат печатки</li>
	<li>шифрування</li>
</ul>
</details>

Заповнив
uaToken
![](image52.png){width=70%}
Залив
![](image53.png){width=70%}
ввів PIN-КОД
![](image54.png){width=70%}

<hr />

<details class="details-info-box_blue details-notice details-notice__hint" style="border-left:3px solid #0000ff; background-color:#f2f5f7; padding:5px;"><summary>на промисловому середовищі</summary><summary></summary>
<p>Перейти в розділ &laquo;Ключі і сертифікати&raquo;.<br />
&mdash; Ввести PIN-код до сховища ключів uacToken (це PIN-код до особистого ключа, що імпортований з ZIP-архіву).<br />
&mdash; Навпроти кожного сертифікату натиснути на кнопку &laquo;Імпортувати&raquo;.</p>
</details>

<https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu>

<hr />

6. Створення ключа автентифікації для шлюзу безпечного обміну
   Шлюз безпечного обміну повинен автентифікуватися при відправці повідомлень до інших шлюзів безпечного обміну. Сертифікат автентифікації використовується для перевірки автентичності шлюзу безпечного обміну.
   Перейти в розділ «Ключі і сертифікати».
   — Обрати токен «softToken-0», натиснувши на нього мишкою.
   — Натиснути на кнопку «Генерувати ключ».
   — Ввести позначку для ключа автентифікації. Рекомендовано ввести позначку authKey.
   — Натиснути на кнопку «OK».
   ![](image55.png){width=70%}
   https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu

<hr />

7. Генерація та подача запиту на сертифікат (Certificate Signing Request (CSR)) для ключа автентифікації
   Перейти в розділ «Ключі і сертифікати».
   — Обрати ключ автентифікації, згенерований на попередньому кроці (authKey).
   — Натиснути на кнопку «Генерувати CSR» - відкриється діалог «Створити запит на підпис сертифіката».
   — У діалоговому вікні необхідно встановити наступні значення:

   | **Поле** | **Значення** |
   | --- | --- |
   | Використання (Usage) | Auth |
   | Сервіс сертифікації (Certification Service) | Необхідно обрати технологічний центр сертифікації ключів відповідного середовищаСЕВДЕІР:<br />«**Trembita Diia CA**» - для промислового середовища,<br />«**Trembita CA Diia TEST**» - для тестового. |
   | CSR Format | PEM |

   за замовчування
   ![](image64.png){width=70%}

   Змінюю
   ![](image65.png){width=70%}
   Заповнив
   ![](image66.png){width=70%}
   Погоджуємося
   ![](image67.png)
   Подаємо "Технічні заявки (регламент)"
   **Видача нового сертифікату автентифікації**
   — прикріплюємо SCR

   Тестове середовище
   <https://cabinet.trembita.gov.ua/new-application/1>

   Промислове середовище
   <https://cabinet.trembita.gov.ua/new-application/10>

   <span style="background-color:palegreen;">— </span><span style="background-color:palegreen;">[Адмін виконує заявку](https://project.trembita.gov.ua:8443/articles/HD-A-3/Admin-robota-z-yadrom-priyednannya-kliyenta#vidacha-novogo-sertifikatu-avtentifikaciyi)</span><span style="background-color:palegreen;"> **"**</span><span style="background-color:palegreen;">**Видача нового сертифікату автентифікації"**</span>

   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu>

<hr />

8. Імпорт нового сертифіката автентифікації на шлюз безпечного обміну
   [(Адмін - робота з ядром) приєднання клієнта](https://project.trembita.gov.ua:8443/articles/HD-A-3/Admin-robota-z-yadrom-priyednannya-kliyenta "HD-A-3: (Адмін - робота з ядром) приєднання клієнта") Виконує пункт
   Перейти в розділ «Ключі і сертифікати».
   — Натиснути на кнопку «Імпорт сертифікату».
   — Натиснути на кнопку «Переглянути» і обрати сертифікат автентифікації, отриманий на попередньому кроці.
   ![](image60.png){width=70%}
   Після завантаження
   ![](image61.png){width=70%}
   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu>

<hr />

9. Активація сертифікатів автентифікації та підпису.
   На цьому етапі сертифікати автентифікації та електронної печатки вже імпортовані до шлюзу безпечного обміну, однак, вони за замовчуванням відключені (в колонці «OCSP-відповідь» для сертифікату вказано як «відключений»). Відключені сертифікати не використовуються шлюзом безпечного обміну.

   Для їх активації необхідно
   Перейти в розділ «Ключі і сертифікати».
   — Обрати **сертифікат автентифікації**, який імпортовано на попередньому кроці (наступний рядок під authKey, з числовим серійним номером).
   — Натиснути на кнопку «Активувати».
   — Обрати **сертифікат печатки** (під рядком «uaToken-sign (sign)»).
   — Натиснути на кнопку «Активувати».
   ![](image62.png){width=70%}
   sign
   Імпортував так як раніше не імпортував.
   ![](image63.png){width=70%}
   <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu>

<hr />

10. Відправка запиту на реєстрацію сертифікатів
    Cтатус сертифікату автентифікації, який імпортовано в попередньому стані «збережений», а не «зареєстровано». Це означає, що цей сертифікат ще не відправлений до серверу каталогу Учасників.

    Для реєстрації сертифікату автентифікації та сертифікату шифрування
    ***Перейти в розділ «Ключі і сертифікати».***
    — Обрати **сертифікат шифрування** (рядок під «uaToken-encr (encr)»).
    — Натиснути на кнопку «Зареєструвати».
    ![](image36.png){width=70%}
    — Обрати **сертифікат автентифікації**, який імпортовано на попередньому кроці.
    відкриється діалог «Запит на реєстрацію».
    ![](image37.png){width=70%}
    Буде надпис запит надіслано
    ![](image69.png){width=70%}
    Обидва в процесі
    ![](image39.png){width=70%}
    Ввести загальнодоступну (публічну) IP-адресу шлюзу безпечного обміну, або відповідне DNS-ім’я
    — Натиснути на кнопку «Зареєструвати»

    Якщо все зроблено коректно, статус сертифікату автентифікації повинен змінитися на «в процесі реєстрації» - це означає, що запит був успішно відправлений шлюзом безпечного обміну.

    Наступним кроком є подача заявки на реєстрацію шлюзу безпечного обміну відповідно до п. 7.4 Регламенту роботи СЕВДЕІР,
    [Реєстрація ШБО в ядрі системи (Тестове середовище)](https://cabinet.trembita.gov.ua/new-application/2)

    [Реєстрація ШБО в ядрі системи (Промислове середовище)](https://cabinet.trembita.gov.ua/new-application/11)

    після чого Адміністратор СЕВДЕІР повинен обробити її та підтвердити запит.

    <span style="background-color:palegreen;">— </span><span style="background-color:palegreen;">[Адмін виконує заявку](https://project.trembita.gov.ua:8443/articles/HD-A-3/Admin-robota-z-yadrom-priyednannya-kliyenta#reyestraciya-shbo-v-yadri-sistemi)</span><span style="background-color:palegreen;"> </span><span style="background-color:palegreen;">**"Реєстрація ШБО в ядрі системи"**</span>

    Коли запит на реєстрацію схвалено, статус сертифікату автентифікації та сертифікату шифрування повинен бути змінений на «registered».

    ![](image1.png){width=70%}
    Мій
    ![](image68.png){width=70%}

    <https://docs.trembita.gov.ua/books/instrukciya-z-instalyaciyi-komponentiv-sistemi-trembita/page/rejestraciya-slyuzu-bezpecnogo-obminu>
