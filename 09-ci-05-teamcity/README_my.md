Виртуальные машины:

![alt text](VMs.png)


Выполнение ansible-playbook:

![alt text](nexus_ansible.png)


Авторизация агента:

![alt text](TC_Authorized.png)




Основная часть
1.Создайте новый проект в teamcity на основе fork.
2.Сделайте autodetect конфигурации.
3.Сохраните необходимые шаги, запустите первую сборку master.

![alt text](Build1.png)

4.Поменяйте условия сборки: если сборка по ветке master, то должен происходит mvn clean deploy, иначе mvn clean test.
5.Для deploy будет необходимо загрузить settings.xml в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.

![alt text](<clean deploy.png>)


![alt text](<settings file.png>)


6.В pom.xml необходимо поменять ссылки на репозиторий и nexus.

![alt text](pom.png)

![alt text](Nexus.png)


