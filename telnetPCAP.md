## Практичне завдання з Network Forensics
### Telnet передає логін/пароль у відкритому вигляді. 
### Перехоплення Telnet у Wireshark

#### Мета 

- перехопити трафік Telnet

- витягнути логін і пароль

- навчитися читати plaintext протоколи

### Підготовка середовища

1. ВМ в одній мережі (більш реальним був би приклад з додаванням ВМ для моніторингу)

Attacker: Kali Linux

Victim: Ubuntu (telnet server)


2. Перевірка Telnet

На Kali:

telnet <IP_жертви>

має з’явитись:

login:
password:

### Захоплення трафіку

На Kali:

- Запустити Wireshark

- Обрати інтерфейс (eth0)

- Натиснути Start Capture

### Виконання атаки

З Kali Linux:

telnet 192.168.88.21

ввести:

login: student
password: 123456

![alt text](image-2.png)

### Аналіз у Wireshark
1. Фільтр
tcp.port == 23
2. Знайти Telnet пакети

Шукати:

Telnet Data

Data (ASCII)

3. Позначити один з рядків Telnet 

Right click → Follow → TCP Stream

![alt text](image.png)

### Результат

Побачите трохи в специфічному вигляді:

login: student
password: 123456

![alt text](image-1.png)



### Чому це працює

Telnet:

❌ не шифрує трафік

❌ передає ASCII

❌ легко аналізується
