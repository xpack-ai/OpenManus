# 설치 방법

두 가지 설치 방법을 제공합니다. **방법 2 (uv 사용)** 이 더 빠른 설치와 효율적인 종속성 관리를 위해 권장됩니다.

## 방법 1: conda 사용

1. 새로운 conda 환경을 생성합니다:

```bash
conda create -n open_manus python=3.12
conda activate open_manus
```

2. 저장소를 클론합니다:

```bash
git clone https://github.com/xpack-ai/OpenManus.git
cd OpenManus
```

3. 종속성을 설치합니다:

```bash
pip install -r requirements.txt
```

## 방법 2: uv 사용 (권장)

1. uv를 설치합니다. (빠른 Python 패키지 설치 및 종속성 관리 도구):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. 저장소를 클론합니다:

```bash
git clone https://github.com/xpack-ai/OpenManus.git
cd OpenManus
```

3. 새로운 가상 환경을 생성하고 활성화합니다:

```bash
uv venv --python 3.12
source .venv/bin/activate  # Unix/macOS의 경우
# Windows의 경우:
# .venv\Scripts\activate
```

4. 종속성을 설치합니다:

```bash
uv pip install -r requirements.txt
```

## 브라우저 자동화 도구 (선택사항)

```bash
playwright install
```

# 설정 방법

OpenManus를 사용하려면 사용하는 LLM API에 대한 설정이 필요합니다. 아래 단계를 따라 설정을 완료하세요:

1. `config` 디렉토리에 `config.toml` 파일을 생성하세요 (예제 파일을 복사하여 사용할 수 있습니다):

```bash
cp config/config.example.toml config/config.toml
```

2. `config/config.toml` 파일을 편집하여 API 키를 추가하고 설정을 커스터마이징하세요:

```toml
# 전역 LLM 설정
[llm]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # 실제 API 키로 변경하세요
max_tokens = 4096
temperature = 0.0

# 특정 LLM 모델에 대한 선택적 설정
[llm.vision]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # 실제 API 키로 변경하세요
```
