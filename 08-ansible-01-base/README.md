1.Попробуйте запустить playbook на окружении из test.yml, зафиксируйте значение, которое имеет факт some_fact для указанного хоста при выполнении playbook.


![alt text](playbook/1.png)

2.Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на all default fact.

![alt text](playbook/2.png)

3.Воспользуйтесь подготовленным (используется docker) или создайте собственное окружение для проведения дальнейших испытаний.

4.Проведите запуск playbook на окружении из prod.yml. Зафиксируйте полученные значения some_fact для каждого из managed host.

![alt text](playbook/3.png)

5.Добавьте факты в group_vars каждой из групп хостов так, чтобы для some_fact получились значения: для deb — deb default fact, для el — el default fact.

6.Повторите запуск playbook на окружении prod.yml. Убедитесь, что выдаются корректные значения для всех хостов.

![alt text](playbook/4.png)

7.При помощи ansible-vault зашифруйте факты в group_vars/deb и group_vars/el с паролем netology.

![alt text](playbook/5.png)

8.Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь в работоспособности.

![alt text](playbook/6.png)

9.Посмотрите при помощи ansible-doc список плагинов для подключения. Выберите подходящий для работы на control node.

ansible-doc -t connection -l

![alt text](playbook/7.png)

10.В prod.yml добавьте новую группу хостов с именем local, в ней разместите localhost с необходимым типом подключения.


  local:
    hosts:
      localhost:
        ansible_connection: local


11.Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь, что факты some_fact для каждого из хостов определены из верных group_vars

ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass

![alt text](playbook/8.png)