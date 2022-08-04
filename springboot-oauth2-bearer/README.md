springboot-oauth-bearer: SpringBoot OAuth2 Resource Server with Keycloak as Provider
======================================================================================

Find detailed info on medium https://ravthiru.medium.com/springboot-oauth2-with-keycloak-for-bearer-client-3a31f608a78

What is it?
-----------

The `springboot-oauth-bearer` demonstrates how to configure Springboot OAUth2 Resource Server
to use Keycloak as Provider. We write a Springboot application providing API which is protected 
with Keycloak. Only Requests with valid tokens can request API.  

System Requirements
-------------------

All you need to build this project is 

* Java 11 (Java SDK 1.11) or later 
*  Gradle
*  Keycloak Server version 16+

Build and Run the springboot-oauth-bearer
--------------------------------------------

1. Open a terminal and navigate to the root directory of this springboot-Keycloak.

2. Build application
   ```
    gradle build
    ```
2. Build and Start springboot-keycloak application using below command

   ````
   gradle bootRun

   ````

Test application
-----------------

docker run -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin -p 9090:8080 jboss/keycloak

## To Get the Token

curl -X POST 'http://localhost:9090/auth/realms/springboot/protocol/openid-connect/token' --header 'Content-Type: application/x-www-form-urlencoded' --data-urlencode 'client_id=demoapp' --data-urlencode 'username=testuser' --data-urlencode 'password=test123' --data-urlencode 'grant_type=password'  
## To Request The API

curl 'http://localhost:8081/employee/101' --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJlSUdjOFhaOHVFUjRJRUowRWpQaG4zR1Rjb2UzeU1MOWJhVDhWd2tjVUR3In0.eyJleHAiOjE2NTk1NzcyOTMsImlhdCI6MTY1OTU3Njk5MywianRpIjoiNzAxZDFjNzUtNDAyYy00ZGZiLTlhZDMtY2RiNDcwYTMxMDgxIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDkwL2F1dGgvcmVhbG1zL3NwcmluZ2Jvb3QiLCJhdWQiOiJhY2NvdW50Iiwic3ViIjoiZTRjZmNjMDEtNzU5OS00ZWE3LWE1NmYtNmM5MjY2ZWU0OWU0IiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiZGVtb2FwcCIsInNlc3Npb25fc3RhdGUiOiIyYTk1ZGMwMC0yZGI4LTRiOTEtOTlkOC1iYWQ1ZjcwYmZjYjYiLCJhY3IiOiIxIiwicmVhbG1fYWNjZXNzIjp7InJvbGVzIjpbIm9mZmxpbmVfYWNjZXNzIiwidW1hX2F1dGhvcml6YXRpb24iLCJkZWZhdWx0LXJvbGVzLXNwcmluZ2Jvb3QiXX0sInJlc291cmNlX2FjY2VzcyI6eyJhY2NvdW50Ijp7InJvbGVzIjpbIm1hbmFnZS1hY2NvdW50IiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6InByb2ZpbGUgZW1haWwiLCJzaWQiOiIyYTk1ZGMwMC0yZGI4LTRiOTEtOTlkOC1iYWQ1ZjcwYmZjYjYiLCJlbWFpbF92ZXJpZmllZCI6ZmFsc2UsInByZWZlcnJlZF91c2VybmFtZSI6InRlc3R1c2VyIn0.eUxRJieZwcdtbPFQByTV5BUuwVFdYVecdesqCvv9DX2OOvNuNHCH3lHujxp4Cev62nkiP2exA3kLKY6u8iFSz2WNpJ7z_MWbGGxXotUZ17tmXrAr22VwYB5q1W9UgXUacZ4S565rY9scYp3DUE1ty0Jnu4fDiuS6SWYbyTmjsuW_O5QMc9Yvjz_cKvGpn-VihCWTEy5u7f8pw84b_TibmOzgWI9B9CDesmIgVvEwdpRFkbP83q6zm7ejwgye9M0D9aS_8RQtZ7IT83jP6DtqndchjlesdFRXl45DZlwiTJ4jmSbS5xrBQhTS4xuyllkNxfv76W0qpBAI6fOCIdzz4Q'


{"access_token":"eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJlSUdjOFhaOHVFUjRJRUowRWpQaG4zR1Rjb2UzeU1MOWJhVDhWd2tjVUR3In0.eyJleHAiOjE2NTk1NzcyOTMsImlhdCI6MTY1OTU3Njk5MywianRpIjoiNzAxZDFjNzUtNDAyYy00ZGZiLTlhZDMtY2RiNDcwYTMxMDgxIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDkwL2F1dGgvcmVhbG1zL3NwcmluZ2Jvb3QiLCJhdWQiOiJhY2NvdW50Iiwic3ViIjoiZTRjZmNjMDEtNzU5OS00ZWE3LWE1NmYtNmM5MjY2ZWU0OWU0IiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiZGVtb2FwcCIsInNlc3Npb25fc3RhdGUiOiIyYTk1ZGMwMC0yZGI4LTRiOTEtOTlkOC1iYWQ1ZjcwYmZjYjYiLCJhY3IiOiIxIiwicmVhbG1fYWNjZXNzIjp7InJvbGVzIjpbIm9mZmxpbmVfYWNjZXNzIiwidW1hX2F1dGhvcml6YXRpb24iLCJkZWZhdWx0LXJvbGVzLXNwcmluZ2Jvb3QiXX0sInJlc291cmNlX2FjY2VzcyI6eyJhY2NvdW50Ijp7InJvbGVzIjpbIm1hbmFnZS1hY2NvdW50IiwibWFuYWdlLWFjY291bnQtbGlua3MiLCJ2aWV3LXByb2ZpbGUiXX19LCJzY29wZSI6InByb2ZpbGUgZW1haWwiLCJzaWQiOiIyYTk1ZGMwMC0yZGI4LTRiOTEtOTlkOC1iYWQ1ZjcwYmZjYjYiLCJlbWFpbF92ZXJpZmllZCI6ZmFsc2UsInByZWZlcnJlZF91c2VybmFtZSI6InRlc3R1c2VyIn0.eUxRJieZwcdtbPFQByTV5BUuwVFdYVecdesqCvv9DX2OOvNuNHCH3lHujxp4Cev62nkiP2exA3kLKY6u8iFSz2WNpJ7z_MWbGGxXotUZ17tmXrAr22VwYB5q1W9UgXUacZ4S565rY9scYp3DUE1ty0Jnu4fDiuS6SWYbyTmjsuW_O5QMc9Yvjz_cKvGpn-VihCWTEy5u7f8pw84b_TibmOzgWI9B9CDesmIgVvEwdpRFkbP83q6zm7ejwgye9M0D9aS_8RQtZ7IT83jP6DtqndchjlesdFRXl45DZlwiTJ4jmSbS5xrBQhTS4xuyllkNxfv76W0qpBAI6fOCIdzz4Q","expires_in":300,"refresh_expires_in":1800,"refresh_token":"eyJhbGciOiJIUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICI1NDFiZTRkZi1mNDk3LTRkNWMtYTg2My0zNzE0MDhjNjNhODUifQ.eyJleHAiOjE2NTk1Nzg3OTMsImlhdCI6MTY1OTU3Njk5MywianRpIjoiZGY4ZmMzOWItZjExOC00YWEyLThiNWQtMjg4ZGEwYjYwOWFjIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo5MDkwL2F1dGgvcmVhbG1zL3NwcmluZ2Jvb3QiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvYXV0aC9yZWFsbXMvc3ByaW5nYm9vdCIsInN1YiI6ImU0Y2ZjYzAxLTc1OTktNGVhNy1hNTZmLTZjOTI2NmVlNDllNCIsInR5cCI6IlJlZnJlc2giLCJhenAiOiJkZW1vYXBwIiwic2Vzc2lvbl9zdGF0ZSI6IjJhOTVkYzAwLTJkYjgtNGI5MS05OWQ4LWJhZDVmNzBiZmNiNiIsInNjb3BlIjoicHJvZmlsZSBlbWFpbCIsInNpZCI6IjJhOTVkYzAwLTJkYjgtNGI5MS05OWQ4LWJhZDVmNzBiZmNiNiJ9.TXsl4UYXw8hJUs5TZHyYok47tyEGiu307vPigMbZN_g","token_type":"Bearer","not-before-policy":0,"session_state":"2a95dc00-2db8-4b91-99d8-bad5f70bfcb6","scope":"profile email"}