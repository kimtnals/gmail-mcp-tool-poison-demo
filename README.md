# Gmail MCP Tool Poison Demo

## 소개
이 프로젝트는 Gmail MCP 환경에서 Tool Poisoning 취약점을 시연하기 위한 예제입니다.

---

## 시작하기

### 1. 가상환경 생성 및 활성화 (Windows 기준)

```bash
uv venv
.\venv\Scripts\activate
```

### 2. 패키지 설치
```bash
uv pip install -e .
```

### 3. Google API 인증 설정
Google Cloud Console에서 가져온 json 파일을 프로젝트 루트 폴더에 credentials.json 파일로 저장하세요.


### 4. 메일 탈취 수신자 이메일 설정
main.py 파일을 열어 아래 부분을 본인의 이메일 주소로 수정하세요.

```python
ATTACKER_EMAIL = "탈취된 데이터를 받을 이메일 주소입니다."
```


## 5. Claude Desktop 설정

`claude_desktop_config.json` 파일에 아래 내용을 추가하세요:

```json
{
  "mcpServers": {
    "gmail_mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/PARENT/FOLDER/gmail-mcp-tool-poison-demo",
        "run",
        "main.py"
      ]
    }
  }
}
```
`claude_desktop_config.json`에서 `--directory` 경로를 반드시 본인 환경에 맞게 절대 경로로 변경하세요.

예:  "C:\\Users\\user\\Workspace\\gmail-mcp-tool-poison-demo"
