---
description: CLOSER의 향상된 최신 기능에 대한 릴리스 정보와 히스토리를 제공합니다
---

# CLOSER 릴리스 정보

본 문서에서는 새로운 기능 / 치명적인 버그 수정 등의 변경점들을 서술합니다.  
눈에 보이지 않는 내부 안정성 개선 등의 변경점들은 본 문서에 작성되지 않았습니다.  

## v0.49.0 - 2020-04-23

#### CLOSER Bot

* \(신규\) [버전 관리 기능](builder/manage/versions.md) 추가
* \(신규\) 사이드바 메뉴 재구성
  * [봇 시스템 메시지 설정](builder/chatbot/system-response.md) 분리
* \(신규\) 봇 편집기 &gt; 저장 오류 시 디자인 개선
* \(신규\) 봇 편집기 &gt; 캔버스에 파라미터 노드, HTTP 요청 노드 등의 내용을 나타내는 메타데이터 표시
* \(신규\) 템플릿 문법 &gt; 메시지 마스킹 도우미 함수\(MASK\) 추가
* \(신규\) 템플릿 문법 &gt; 메시지 QUOTE/ESCAPE 도우미 함수 추가

## v0.48.1 - 2020-04-06

**CLOSER Bot**

* \(신규\) [템플릿 문법](builder/chatbot/advanced/template-syntax/#helper-functions) &gt; [글자 자르기 \(TRUNCATE\) 도우미 함수](builder/chatbot/advanced/template-syntax/helper-function.md#truncate) 추가
* \(신규\) [플로우 연결 노드](builder/chatbot/node/flow.md) 및 [플로우 연결 버튼 ](builder/chatbot/node/response.md#goto-button)설정에서 플로우 목록 드롭다운을 플로우 목록과 같도록 개선
* \(버그 수정\) [뒤로가기 노드](builder/chatbot/node/back.md)와 [플로우 연결 버튼](builder/chatbot/node/response.md#goto-button)을 함께 이용할 경우 뒤로가기 동작이 부자연스러운 오류 수정
* \(버그 수정\) 대시보드 &gt; 활성 사용자 통계 수치가 그래프와 일치하지 않는 오류 수정
* \(버그 수정\) 네이버 톡톡 &gt; [빠른 답장 글자 수 제한](builder/messenger-integrations/limitations.md)이 넘어갈 경우, 메시지 기반의 조건이 동작하지 않는 오류 수정

**CLOSER Chat**

* \(버그 수정\) 자주쓰는 문구 &gt; 템플릿 문법을 이용할 때, 없는 값을 참조하면 아무 동작 없는 오류 수정  

## v0.48.0 - 2020-03-24

**CLOSER Bot**

* \(신규\) 메시지 응답 노드 &gt; [플로우 연결 버튼](builder/chatbot/node/response.md#goto-button) 추가
* \(신규\) 캔버스 &gt; 끌어서 노드 복제 기능 추가 \(Ctrl + 클릭 후 드래그\)
* \(신규\) 템플릿 함수 &gt; [한글 조사\(JOSA\) 도우미 함수](builder/chatbot/advanced/template-syntax/helper-function.md#josa-noun-josa-or-or-or-or-or) 추가

**CLOSER Chat**

* \(신규\) 자주쓰는 문구 &gt; 순서 변경 기능 추가
* \(신규\) 자주쓰는 문구 &gt; [템플릿 문법](builder/chatbot/advanced/template-syntax/) 기능 추가

## v0.47.0 - 2020-03-01

**CLOSER Bot**

* [잠재고객](builder/audience.md) &gt; 공유 링크 생성 기능 추가
* 봇 편집기 &gt; 상단 레이아웃 툴바 구성 변경
  * 개발자 도구 버튼 위치 변경
  * [대화 미리보기](builder/chatbot/bot-editor/preview.md)에 재시작 버튼 추가 

## v0.46.0 - 2019-12-19

#### CLOSER Bot

* 봇 편집기 &gt; [**레이아웃 커스터마이징**](builder/chatbot/bot-editor/#undefined) 기능 추가
* 봇 편집기 &gt; 플로우 캡쳐 기능 추가

## v0.45.0 - 2019-12-06

#### CLOSER Bot

* 봇 편집기 &gt; [**개발자 도구**](builder/chatbot/advanced/inspector.md) **추가**
* 봇 편집기 &gt; [**뒤로가기 노드**](builder/chatbot/node/back.md) **추가**
  * 시험적으로 제공되던 [뒤로가기 스택 노드](builder/chatbot/node/backstack.md)는 지원이 중단될 예정입니다.

## v0.44.2 - 2019-11-25

#### CLOSER Bot

* **카카오톡**에서 `tel:` 또는 `mailto:` URL 입력 시 동작하지 않는 문제 수정
* **페이스북**에서 [지원 중지](https://developers.facebook.com/docs/messenger-platform/send-messages/quick-replies#locations)된 위치 빠른 답장 \(location quick reply\) 제거
* **웹사이트** 연동 시 [초기 파라미터 설정 기능](builder/messenger-integrations/web.md#advanced-initial-parameter) 추가 

#### CLOSER Chat

* 상담원 패널 &gt; 커스텀 패널 설정 &gt; [HTML 설정 방식](chat/settings/conversations.md#html) 추가 

## v0.44.0 - 2019-11-18

#### CLOSER Bot

* 플로우 편집 &gt; 노드 연결 조건에 빠른 제안 추가
  * 성공/실패 여부가 나뉘는 노드 등에서 다음 연결 조건을 빠르게 제안해주는 기능이 추가되었습니다.
* 플로우 편집 &gt; [이메일 노드](builder/chatbot/node/email.md) 추가 \(베타\)
  * 고객의 정보를 기반으로 알림 메일을 보낼 수 있는 노드가 추가되었습니다.
* 봇 생성 템플릿 변경
  * 이제 빈 봇을 생성하면 [일상대화 노드](builder/chatbot/node/chitchat.md)로 구성된 [폴백 플로우](builder/chatbot/flow.md#fallback-flow)가 함께 생성됩니다.
* 카카오톡 오픈빌더 연동 &gt; 상담원 호출 노드 기능 변경
  * 이제 카카오톡 오픈빌더 연동 시 카카오톡이 제공하는 상담원 호출 기능을 사용 가능하도록 변경하였습니다.  

## v0.43.0 - 2019-11-07

#### CLOSER Bot

* 플로우 편집기의 검색 기능 개선
  *  이제 플로우 편집기의 검색 기능이 플로우 제목이 아닌 **전체 노드의 내용까지 검색**하도록 개선되었습니다.

## v0.42.0 - 2019-10-25

#### CLOSER Bot

* [일상대화 노드 ](builder/chatbot/node/chitchat.md)추가 \(베타\)
  * 사용자의 입력에 대해 자동화된 일상대화를 생성하여 반환하는 노드를 추가하였습니다.
* [잠재고객 검색 조건 ](builder/audience.md#undefined)기능 추가 \(베타\)
  * 파라미터 / 메시징 채널 등을 기반으로 검색 결과를 필터링할 수 있는 기능이 추가되었습니다.
* LINE 연동 개선
  * LINE &gt; 메시지에 유니코드 이모지\(🙌\) 포함 시 메시지가 수신되지 않는 오류를 수정하였습니다. 

## v0.41.0 - 2019-09-25

#### CLOSER Bot

* [잠재고객 ](builder/audience.md)페이지 추가 \(베타\)
  * 챗봇과 대화한 사용자들의 목록을 확인할 수 있는 기능을 추가하였습니다.
  * 파라미터 기반 검색 등 다양한 기능이 추가될 예정입니다.
* LINE 연동 개선
  * 좌우로 빈 공간 \(`'  '`\)이 있는 메시지가 처리되지 않는 오류 수정
  * 고객이 보낸 이미지가 표시되지 않는 오류 수정

#### CLOSER Chat

* 오류 수정
  * 상담 화면에서 대기 상담이 나타나지 않다가 갑자기 발생하는 현상 개선 

#### 공통

* Chrome 70 버전 이하 사용자들에게 최신 브라우저 업데이트 권장 알림 표시

## v0.40.0 - 2019-09-15

* 요금제 변경
  * CLOSER 요금 정책이 변경되었습니다.
  * 자세한 사항은 [https://www.closer.ai/\#pricing](https://www.closer.ai/#pricing) 페이지를 참고해주세요.

## v0.39.2 - 2019-08-01

* 버그 수정
  * 모바일 브라우저에서 웹 채팅 이용 시 세로 사이즈가 큰 이미지의 비율이 조정되지 않는 현상 개선
  * 웹 채팅 이용 시 첫 빠른 답장 하단의 일부가 짤려 보이는 현상 개선
  * 텍스트 메시지로 `"{}"`  를 전송하는 경우 발생하는 오류 수정

## v0.39.0 - 2019-07-15

* 서비스 알림 메뉴 추가
  * 공지사항이나 계정 관련 알림, 혹은 새로운 소식 등을 더 쉽게 받아보실 수 있도록 앱 내에 알림 기능을 추가하였습니다.

## v0.38.2 - 2019-07-11

#### CLOSER Chat

* 상담 목록에 **봇 대화 제외하고 보기** 필터 추가
* 통계 파일 다운로드 시 파일명에 팀 / 챗봇 이름 추가

## v0.38.1 - 2019-07-01

#### CLOSER Chat

* 상담 종료 시 참여중인 상담원을 대화에서 퇴장시키되도록 변경

## v0.38.0 - 2019-06-27

#### CLOSER Bot

* 페이스북 연동 &gt; 메신저 하단 **고정 메뉴**와 대화 시작 전 **환영 인삿말** 커스터마이징 기능 추가
  * 봇 연동 설정 &gt; 페이스북 연동 설정 하단의 고급 설정 메뉴를 통해 이용 가능합니다. 

#### CLOSER Chat

* **상담 자동 종료** 기능 추가
  * 오랜 시간 응답이 없거나 응대하지 못한 상담 등을 자동으로 종료할 수 있습니다.  팀 설정에서 이용 가능합니다.

## v0.37.4 - 2019-06-10

#### CLOSER Bot

* 구글 스프레드시트 노드의 spreadSheetId 값에 `-`문자를 입력할 수 없던 오류상 수정

## v0.37.0 - 2019-05-15

#### CLOSER Bot

* 플로우 편집기의 저장 방식 변경
  * 저장하지 않아도 동시에 여러 플로우를 수정 가능하도록 수정사항 관리 구조를 개선하였습니다.
* 플로우 편집기에 팝업 노드 팔레트 추가
  * 빈 공간에 새로운 연결을 끌어다 놓을 경우 간편하게 새로운 노드를 추가할 수 있도록 개선되었습니다. 

## v0.36.0 - 2019-04-05

#### CLOSER Bot

* 메시지 응답 노드의 입력 양식 개선
  * 카드 형태나 미디어 형태의 메시지를 더욱 직관적으로 편집할 수 있도록 입력 양식을 개선하였습니다.
* 메시지 응답 노드에 첨부파일 지원
  * 크기가 작은 이미지 파일을 CLOSER에 직접 업로드할 수 있도록 개선하였습니다.
* 사용자 입력 요청 노드 입력 양식 개선
  * 웹 링크 / 포스트백 버튼 등의 데이터를 더 직관적으로 편집할 수 있도록 입력 양식을 개선하였습니다. 

## v0.35.0 - 2019-02-23

#### CLOSER Bot

* 카카오 오픈빌더 스킬 응답 API v2 로 마이그레이션
* CLOSER embedded chat의 선택지 입력 UI를 말풍선 내부 버튼에서 빠른 답장\(quick reply\)형태로 변경
* 메신저에서 지원하지 않는 미디어 혹은 잘못된 미디어 메시지를 해당 미디어의 유형\(사진, 영상, 음성 등\)을 나타내는 placeholder 이미지로 바꾸어 전달되도록 변경 



