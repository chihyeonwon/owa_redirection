# OWA 리디렉션 분석 보고서

## 개요
OWA (Outlook Web App) 리디렉션은 사용자가 HTTP를 통해 OWA에 접근하려고 할 때 HTTPS로 자동으로 리디렉션하는 방법입니다. 이 보고서에서는 OWA 리디렉션의 원리, 설정 방법, 그리고 분석 결과에 대해 설명합니다.

## OWA 리디렉션 원리
OWA 리디렉션은 사용자가 HTTP를 통해 OWA에 접근하려고 할 때, 이를 HTTPS로 자동으로 리디렉션하여 보안을 강화하는 방법입니다. 이를 통해 사용자는 안전하게 OWA에 접근할 수 있습니다.

## 설정 방법
OWA 리디렉션은 다음과 같은 단계로 설정할 수 있습니다:
1. 기본 웹 사이트에서 SSL 필요 설정 제거
2. 기본 웹 사이트의 다른 가상 디렉터리에서 SSL 필요 설정 복원
3. 기본 웹 사이트를 구성하여 /owa 가상 디렉터리로 리디렉션
4. 기본 웹 사이트의 모든 가상 디렉터리에서 HTTP 리디렉션 제거
5. IIS를 다시 설정하여 변경 내용 적용

### 단계별 설정
1. **SSL 필요 설정 제거**:
   - IIS 관리자에서 기본 웹 사이트를 선택하고, SSL 설정 페이지에서 SSL 필요 확인란의 선택을 취소합니다.
   - 명령줄에서 다음 명령을 실행하여 설정을 제거할 수 있습니다:
     ```shell
     %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site" -section:access -sslFlags:None -commit:APPHOST
     ```

2. **다른 가상 디렉터리에서 SSL 필요 설정 복원**:
   - 기본 웹 사이트의 다른 가상 디렉터리에서 SSL 필요 설정을 복원합니다.

3. **기본 웹 사이트 구성**:
   - 기본 웹 사이트를 구성하여 HTTP 요청을 /owa 가상 디렉터리로 리디렉션합니다.

4. **HTTP 리디렉션 제거**:
   - 기본 웹 사이트의 모든 가상 디렉터리에서 HTTP 리디렉션을 제거합니다.

5. **IIS 다시 설정**:
   - IIS를 다시 설정하여 변경 내용을 적용합니다.

## 분석 결과
OWA 리디렉션을 통해 사용자가 HTTP를 통해 OWA에 접근하려고 할 때, 이를 HTTPS로 자동으로 리디렉션하여 보안을 강화할 수 있음을 확인하였습니다.

## 결론
OWA 리디렉션 설정을 통해 사용자가 안전하게 OWA에 접근할 수 있도록 보안을 강화할 수 있습니다. 이를 통해 네트워크 관리자는 사용자들의 보안 문제를 효과적으로 해결할 수 있습니다.

## 참고 자료
- [Exchange Server 웹용 Outlook 대한 http to https 리디렉션 구성](https://learn.microsoft.com/ko-kr/exchange/clients/outlook-on-the-web/http-to-https-redirection?view=exchserver-2019)
- [Outlook Web App (OWA) HTTP to HTTPS Redirection](https://itblog.ldlnet.net/index.php/2019/10/07/outlook-web-app-owa-http-to-https-redirection/)

---
