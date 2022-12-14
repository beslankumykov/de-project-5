# Проект 5

### Описание
Репозиторий предназначен для сдачи проекта №5.

### Как работать с репозиторием
1. В вашем GitHub-аккаунте автоматически создастся репозиторий `de-project-5` после того, как вы привяжете свой GitHub-аккаунт на Платформе.
2. Скопируйте репозиторий на свой компьютер. В качестве пароля укажите ваш `Access Token`, который нужно получить на странице [Personal Access Tokens](https://github.com/settings/tokens)):
	* `git clone https://github.com/{{ username }}/de-project-5.git`
3. Перейдите в директорию с проектом: 
	* `cd de-project-5`
4. Выполните проект и сохраните получившийся код в локальном репозитории:
	* `git add .`
	* `git commit -m 'my best commit'`
5. Обновите репозиторий в вашем GutHub-аккаунте:
	* `git push origin main`

### Структура репозитория
Вложенные файлы в репозиторий будут использоваться для проверки и предоставления обратной связи по проекту. Поэтому постарайтесь публиковать ваше решение согласно установленной структуре — так будет проще соотнести задания с решениями.

Внутри `src` расположены две папки:
- `/src/dags`, папка для python кода ваших dag для airflow. Здесь необходимо размещать файлы разрешением `'.py'`;
- `/src/sql`, папка для sql кода ваших скриптов для базы данных Vertica. Здесь необходимо размещать файлы с разрешением `'.sql'`.

Для удобства проверки рекомендуем именовать файлы согласно шагам, например, для шага 1 в задании нужно создать файл с названием `'1_*.py'` и так далее.

### Как запустить контейнер
Запустите локально команду:
```
docker run \
-d \
-p 3000:3000 \
-p 3002:3002 \
-p 15432:5432 \
--mount src=airflow_sp5,target=/opt/airflow \
--mount src=lesson_sp5,target=/lessons \
--mount src=db_sp5,target=/var/lib/postgresql/data \
--name=de-sprint-5-server-local \
sindb/de-pg-cr-af:latest
```

После того как запустится контейнер, вам будут доступны:
- Airflow
	- `localhost:3000/airflow`
- БД
	- `jovyan:jovyan@localhost:15432/de`
