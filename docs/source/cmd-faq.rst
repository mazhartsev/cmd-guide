
.. _cmd-faq:

Часто задаваемые вопросы
=======================================

В данном разделе содержатся ответы на часто задаваемые вопросы. Все рассмотренные вопросы содержат ответы по сути, без лишней теории. За разъяснениями и дополнительной информацией обращайтесь к предыдущим разделам данного руководства.


Как отключить/включить контроль учетных записей (UAC) через командную строку?
-----------------------------------------------------------------------------

Отключение::
    
    /k reg ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 0 /f
    
    
    
Включение::

    /k reg ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 1 /f


Как скопировать лицензию КриптоПро из реестра
--------------------------------------------------------

Ниже приведен список команд для каждой из версий КриптоПро. Команды позволяют извлечь номер лицензии КриптоПро из реестра в текстовый файл на рабочем столе. Достаточно просто скопировать команду в cmd. После ее выполнения на рабочем столе появится txt файл ``CProX.X-license.txt`` с номером лицензии. Пример содержания файла::

    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\05480A45343B0B0429E4860F13549069\InstallProperties
    ProductID    REG_SZ    3636GN000001D1X5FUННU6Q43

Строка напротив параметра ``ProductID`` и будет значением лицензии, в моем случае это ``3636GN000001D1X5FUННU6Q43``.

**Команды**

3.6::

    reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\05480A45343B0B0429E4860F13549069\InstallProperties\ /v ProductID >> %CD%/Desktop/CPro3.6-license.txt

3.9::

    reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\68A52D936E5ACF24C9F8FE4A1C830BC8\InstallProperties\ /v ProductID >> %CD%/Desktop/CPro3.9-license.txt

4.0::

    reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\7AB5E7046046FB044ACD63458B5F481C\InstallProperties\ /v ProductID >> %CD%/Desktop/CPro4.0-license.txt

3.0::

    reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\0CC4F742C3275A04A9832E2E2CD4BE64\InstallProperties /v ProductID >> %CD%/Desktop/CPro3.0-license.txt
    
    
Экспорт контейнера закрытого ключа из реестра
-------------------------------------------------------------

Для 32-битных систем::

    reg export "hklm\SOFTWARE\Crypto Pro\Settings\Users\{SID-пользователя}\Keys" keys.reg /y
    
Для 64-битных систем::

    reg export "hklm\SOFTWARE\Wow6432Node\Crypto Pro\Settings\Users\{SID-пользователя}\Keys" keys.reg /y
    
Как узнать SID текущего пользователя?
-------------------------------------

::

    WHOAMI /USER

Импорт контейнера закрытого ключа в реестр
----------------------------------------------------

::

    reg import keys.reg




