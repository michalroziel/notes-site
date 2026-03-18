# API Endpoint Inventar

_Automatisch aus Spring-Controller-Annotationen generiert._

## Edge

| Methode | Pfad | Path-Parameter | Query-Parameter | Header | Request-[[Body]] | Response-Codes | Response-Format | Beschreibung |
|---------|------|----------------|-----------------|--------|--------------|----------------|-----------------|--------------|
| DELETE | /api/edge/admin/cache/all | – | – | – | – | 200 | JSON | Leert den gesamten Cache. |
| DELETE | /api/edge/admin/cache/files/{path:.+} | path:String (pflicht) | – | – | – | 200, 400 | JSON | Invalidiert eine einzelne Datei im Cache. |
| DELETE | /api/edge/admin/cache/prefix | – | value:String (pflicht) | – | – | 200, 400 | JSON | Invalidiert alle Cache-Einträge mit dem gegebenen Pfad-Prefix. |
| GET | /api/edge/admin/config | – | – | – | – | 200 | JSON | getConfig |
| PATCH | /api/edge/admin/config | – | – | – | ConfigPatchDto | 200, 400 | JSON | Partielles Config-Update (nur gesetzte Felder werden übernommen). |
| PUT | /api/edge/admin/config | – | – | – | ConfigDto | 200, 400 | JSON | Vollständiges Config-Update (ersetzt alle Felder). |
| DELETE | /api/edge/admin/config/ttl | – | prefix:String (pflicht) | – | – | 200 | JSON | Entfernt eine TTL-Policy. |
| GET | /api/edge/admin/config/ttl | – | – | – | – | 200 | JSON | getTtlPolicies |
| PUT | /api/edge/admin/config/ttl | – | – | – | TtlPolicyDto | 200 | JSON | Setzt eine TTL-Policy für einen Pfad-Prefix. |
| GET | /api/edge/admin/stats | – | windowSec:int (optional, default=60) | – | – | 200 | JSON | Liefert einen Metriken-Snapshot der Edge-Node. |
| GET | /api/edge/files/{*path} | path:String (pflicht) | – | Range:String (optional) | – | 200, 206, 400, 502, variabel | Binary | Liefert eine Datei aus dem Cache oder vom Origin. |
| HEAD | /api/edge/files/{*path} | path:String (pflicht) | – | – | – | 200, 400, 502, variabel | Kein Body | Liefert nur die HTTP-Header einer Datei (kein Body). |
| GET | /api/edge/health | – | – | – | – | 200 | JSON | health |
| GET | /api/edge/info | – | – | – | – | 200 | JSON | Gibt Region und aktuelle Konfigurationsparameter zurück. |
| GET | /api/edge/ready | – | – | – | – | 200 | JSON | ready |

## Origin

| Methode | Pfad | Path-Parameter | Query-Parameter | Header | Request-Body | Response-Codes | Response-Format | Beschreibung |
|---------|------|----------------|-----------------|--------|--------------|----------------|-----------------|--------------|
| GET | /api/origin/admin/config | – | – | – | – | 200 | JSON | get |
| PATCH | /api/origin/admin/config | – | – | – | OriginConfigPatchDto | 200, 400 | JSON | Partielles Runtime-Update ohne Neustart. |
| DELETE | /api/origin/admin/files/{*path} | path:String (pflicht) | – | – | – | 204, 404 | Kein Body | delete |
| PUT | /api/origin/admin/files/{*path} | path:String (pflicht) | – | – | byte[] | 204, 413 | Kein Body | put |
| GET | /api/origin/files | – | page:int (optional, default=1)<br>size:int (optional, default=20) | – | – | 200, 400 | JSON | list |
| GET | /api/origin/files/{*path} | path:String (pflicht) | – | – | – | 404 | Binary | get |
| HEAD | /api/origin/files/{*path} | path:String (pflicht) | – | – | – | 404 | Kein Body | head |
| GET | /api/origin/health | – | – | – | – | 200 | JSON | health |
| GET | /api/origin/ready | – | – | – | – | 200 | JSON | ready |

## Router

| Methode | Pfad | Path-Parameter | Query-Parameter | Header | Request-Body | Response-Codes | Response-Format | Beschreibung |
|---------|------|----------------|-----------------|--------|--------------|----------------|-----------------|--------------|
| GET | /api/cdn/admin/audit | – | userId:long (pflicht)<br>from:String (optional)<br>to:String (optional)<br>action:String (optional)<br>result:String (optional) | – | – | 200 | JSON | Liefert Audit-Logs eines spezifizierten Users als JSON-Liste. |
| GET | /api/cdn/admin/audit/export | – | userId:long (pflicht)<br>from:String (optional)<br>to:String (optional)<br>action:String (optional)<br>result:String (optional) | – | – | 200 | text/csv | Exportiert Audit-Logs eines spezifizierten Users als CSV. |
| DELETE | /api/cdn/admin/cache/region/{region}/all | region:String (pflicht) | – | – | – | – | Kein [[Body]] | Entfernt den kompletten Cache einer Region. |
| DELETE | /api/cdn/admin/cache/region/{region}/[[Files]]/{path:.+} | region:String (pflicht)<br>path:String (pflicht) | – | – | – | – | Kein Body | Invalidiert eine konkrete Datei in der angegebenen Region. |
| DELETE | /api/cdn/admin/cache/region/{region}/prefix | region:String (pflicht) | value:String (pflicht) | – | – | – | Kein Body | Invalidiert alle Dateien mit dem angegebenen Prefix in der Region. |
| GET | /api/cdn/admin/edges/managed | – | – | – | – | 200 | Kein Body | Listet alle verwalteten Edge-Instanzen. |
| DELETE | /api/cdn/admin/edges/region/{region} | region:String (pflicht) | deregister:boolean (optional, default=true) | – | – | 200, 400, 404 | JSON | Stoppt alle managed Edges einer Region. |
| POST | /api/cdn/admin/edges/start | – | – | – | StartEdgeRequest | 201, 409 | JSON | Startet eine verwaltete Edge-Instanz. |
| POST | /api/cdn/admin/edges/start/auto | – | – | – | AutoStartEdgesRequest | 201, 409 | JSON | Startet mehrere Edge-Instanzen automatisch. |
| DELETE | /api/cdn/admin/edges/{instanceId} | instanceId:String (pflicht) | deregister:boolean (optional, default=true) | – | – | 200, 404 | JSON | Stoppt eine verwaltete Edge-Instanz. |
| GET | /api/cdn/admin/files | – | page:int (optional, default=1)<br>size:int (optional, default=20) | – | – | variabel | JSON | Listet alle Dateien im Origin auf (inkl. Pagination). Ruft den Origin direkt über den Router-Admin-API-Endpunkt ab. |
| DELETE | /api/cdn/admin/[[Files]]/{*path} | path:String (pflicht) | region:String (optional) | – | – | 204, variabel | JSON | Löschen einer Datei vom Origin und invalidieren aller Edge-Caches in der Region (oder global). |
| GET | /api/cdn/admin/[[Files]]/{*path} | path:String (pflicht) | – | – | – | variabel | JSON | Zeigt Metadaten einer Datei im Origin an. Ruft den Origin direkt über den Router-Admin-API-Endpunkt ab. |
| PUT | /api/cdn/admin/[[Files]]/{*path} | path:String (pflicht) | region:String (optional) | – | byte[] | 200, variabel | JSON | Hochladen einer Datei zum Origin und invalidieren aller Edge-Caches in der Region (oder global). |
| GET | /api/cdn/admin/origin/cluster | – | checkHealth:boolean (optional, default=false) | – | – | 200 | JSON | getCluster |
| POST | /api/cdn/admin/origin/failover/check | – | – | – | – | 200 | JSON | runFailoverCheck |
| POST | /api/cdn/admin/origin/promote | – | url:String (pflicht) | – | – | 200, 400, 404 | JSON | promote |
| DELETE | /api/cdn/admin/origin/spares | – | url:String (pflicht) | – | – | 204, 400, 404 | JSON | removeSpare |
| POST | /api/cdn/admin/origin/spares | – | url:String (pflicht) | – | – | 201, 400 | JSON | addSpare |
| GET | /api/cdn/admin/stats | – | windowSec:int (optional, default=60)<br>aggregateEdge:boolean (optional, default=true) | – | – | 200 | JSON | Liefert aggregierte Statistikdaten für den angegebenen Zeitbereich. |
| GET | /api/cdn/admin/users | – | – | – | – | 200 | JSON | Liefert alle vorhandenen Benutzer. |
| POST | /api/cdn/admin/users | – | – | – | CreateUserRequest | 200, 400, 409 | JSON | Legt einen neuen Benutzer an. |
| DELETE | /api/cdn/admin/users/{id} | id:long (pflicht) | – | – | – | 204, 404 | Kein Body | Löscht einen Benutzer anhand seiner technischen ID. |
| POST | /api/cdn/auth/login | – | – | – | LoginRequest | 200, 400, 404 | JSON | Führt einen Login anhand des übergebenen Benutzernamens durch. |
| GET | /api/cdn/files/{*path} | path:String (pflicht) | region:String (optional)<br>clientId:String (optional) | X-Client-Region:String (optional)<br>X-Client-Id:String (optional)<br>X-User-Id:String (optional) | – | 400, 503, variabel | JSON | Routet eine Datei zu einer passenden Edge-Instanz und setzt Redirect-Header. |
| GET | /api/cdn/health | – | – | – | – | 200 | JSON | Einfacher Liveness-Endpunkt für Orchestrierung und Monitoring. |
| GET | /api/cdn/ready | – | – | – | – | 200 | JSON | Readiness-Endpunkt, der die Betriebsbereitschaft des Routers signalisiert. |
| DELETE | /api/cdn/routing | – | region:String (pflicht)<br>url:String (pflicht) | – | – | 200, 404 | JSON | Entfernt eine Edge-Instanz aus der Region. |
| GET | /api/cdn/routing | – | checkHealth:boolean (optional, default=false) | – | – | 200 | JSON | Liefert den aktuellen Routing-Index. |
| POST | /api/cdn/routing | – | region:String (pflicht)<br>url:String (pflicht) | – | – | 201 | Kein [[Body]] | Fuegt eine Edge-Instanz zur Region hinzu. |
| POST | /api/cdn/routing/bulk | – | – | – | List<BulkRequest> | 200 | JSON | Fuehrt mehrere Routing-Updates in einem Request aus. |
| GET | /api/cdn/stats | – | windowSec:int (optional, default=60) | X-User-Id:String (optional) | – | 200, 401 | JSON | Liefert eine aggregierte Statistik für ein Zeitfenster. |
| GET | /api/cdn/stats/file/{fileId} | fileId:long (pflicht) | – | X-User-Id:String (optional) | – | 200, 400, 401, 404 | JSON | Liefert Detaildaten für eine Datei-ID aus der aktuellen Rangliste. |
| GET | /api/cdn/stats/[[Files]] | – | limit:int (optional, default=10) | X-User-Id:String (optional) | – | 200, 401 | JSON | Liefert die Top-Dateien nach Download-Anzahl. |

Hinweise:
- `Response-Codes` werden heuristisch aus `ResponseEntity`-Aufrufen im Code erkannt.
- `variabel` bedeutet: der endgültige Statuscode wird indirekt zur Laufzeit bestimmt.
