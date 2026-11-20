# Л08: Docker Compose (Многоконтейнерные приложения)

## Цель
Изучить Docker Compose для управления многоконтейнерными приложениями. Собрать два стека: веб-приложение (Flask + Redis) и систему мониторинга (Prometheus + Grafana + Blackbox).

## Структура проекта
- `flask_app/` — первый стек (Python Flask + Redis).
- `monitoring/` — второй стек (Prometheus, Grafana, Blackbox).

## Ход выполнения

### Стек 1: Flask + Redis (Счетчик посещений)
В папке `flask_app` создан `compose.yaml`, описывающий два сервиса. Приложение Flask ходит в Redis по DNS-имени `redis`.
Запуск стека:
```bash
cd flask_app
sudo docker compose up -d
```
Проверка работы через curl (счетчик увеличивается при каждом запросе):

<img width="903" height="931" alt="Снимок экрана 2026-11-20 164621" src="https://github.com/user-attachments/assets/dc60cd0c-af4c-4491-b5dc-259465704bd8" />

<img width="898" height="423" alt="Снимок экрана 2026-11-20 164637" src="https://github.com/user-attachments/assets/108f5990-45ee-4199-84be-054847a39440" />

<img width="902" height="130" alt="Снимок экрана 2026-11-20 164729" src="https://github.com/user-attachments/assets/a91855b9-7b5c-4182-854a-99e0bc337c2f" />

### Стек 2: Prometheus + Grafana + Blackbox
В папке monitoring создан compose.yaml с тремя сервисами и конфигурационные файлы prometheus.yml и blackbox.yml для сбора метрик доступности.
Запуск стека:
```bash
cd monitoring
sudo docker compose up -d
```
Проверка статуса контейнеров:
<img width="902" height="764" alt="Снимок экрана 2026-11-20 165417" src="https://github.com/user-attachments/assets/88bb8569-9664-4c4a-b83d-fb506b09505a" />
<img width="894" height="175" alt="Снимок экрана 2026-11-20 171617" src="https://github.com/user-attachments/assets/0f0f396e-9819-4150-ae1c-ee527bd479be" />

Интерфейс Prometheus доступен на порту 9090:
<img width="914" height="582" alt="Снимок экрана 2026-11-20 171646" src="https://github.com/user-attachments/assets/559e71ef-b5c5-44ae-a4f4-a136eb8eead3" />

## Итог
Отработаны команды docker compose up -d, docker compose ps. Изучен принцип описания многоконтейнерных сред в едином compose.yaml и организация сети между контейнерами.
