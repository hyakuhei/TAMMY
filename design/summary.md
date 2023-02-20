## High Level Architecture
![High Level Architecture](output/High%20Level%20Architecture.png)

| Actor | Description |
| --- | ---- |
| browser | User's web browser |
| django | Python django framework |
| dynamic_store | User generated content |
| gunicorn | Gunicorn webserver in front of django |
| jtg | The LTM renderer |
| ltm | Lightweight Threat Modeller - generates JSON |
| md-block | Publicly available Markdown to HTML library - pulled via CDN |
| nginx | Front end proxy |
| static_store | Content created by TAMMY developers |


## User visits TAMMY.net
![User visits TAMMY.net](output/User%20visits%20TAMMY.net.png)

| Id | From | To | Data |
| --- | ---- | --- | ---- |
| 1 | browser | nginx | GET / |
| 2 | nginx | static_store | Fetch index.html |
| 3 | nginx | browser | Static Content with MD Library |
| 4 | browser | md-block | Fetch Markdown Rendering Library |


## User submits LTM
![User submits LTM](output/User%20submits%20LTM.png)

| Id | From | To | Data |
| --- | ---- | --- | ---- |
| 1 | browser | nginx | POST ltm string |
| 2 | nginx | gunicorn | POST ltm string |
| 3 | gunicorn | django | Route ltm string |
| 4 | django | ltm | Parse ltm string to JSON |
| 5 | django | jtg | Generate images, Markdown |
| 6 | jtg | dynamic_store | Store images, Markdown |
| 7 | django | gunicorn | Link to Markdown in dynamic_sto |
| 8 | gunicorn | nginx | Link to Markdown in dynamic_store |
| 9 | nginx | browser | Markdown link |
| 10 | browser | browser | Render |
| 11 | browser | nginx | GET /markdown link |
| 12 | nginx | dynamic_store | GET /markdown link |


