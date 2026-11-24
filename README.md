# KGB Gateway

## G28에서 Board API 확인

G28의 브라우저에서 [Swagger UI](http://localhost:8000/swagger-ui/index.html)를 열고 서비스 목록에서 `kgb-board`를 선택합니다. `GET /api/boards`에서 **Try it out → Execute**를 누르면 Gateway를 경유한 게시판 목록을 확인할 수 있습니다. 같은 개발망의 다른 PC에서는 `localhost`를 G28의 개발망 주소로 바꿉니다.

| 용도 | Gateway 경로 |
|---|---|
| Board OpenAPI 명세 | `/kgb-board/v3/api-docs` |
| 게시판 목록 | `/kgb-board/api/boards` |
| Board 메트릭 | `/kgb-board/actuator/prometheus` |

G28의 PowerShell에서 아래 명령으로 API 응답을 확인할 수 있습니다.

```powershell
Invoke-RestMethod http://localhost:8000/kgb-board/api/boards
```

G28의 Docker Desktop에서 실행하는 Prometheus는 `host.docker.internal:8000`을 대상으로 `/kgb-board/actuator/prometheus`를 수집합니다. 실제 수집 성공 여부는 Prometheus에서 `up{job="kgb-board"}` 값이 `1`인지 확인합니다.
