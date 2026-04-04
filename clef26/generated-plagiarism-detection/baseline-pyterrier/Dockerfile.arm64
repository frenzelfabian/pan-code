# See .devcontainer/Dockerfile.dev.
FROM arm64v8/ubuntu

RUN apt-get update && apt-get install -y openjdk-11-jdk python3 python3-pip git

ADD requirements.txt /

# Install dependencies and ensure pyterrier resources are cached
RUN pip3 install -r /requirements.txt --break-system-packages \
    && rm /requirements.txt \
    && python3 -c 'from tira.third_party_integrations import ensure_pyterrier_is_loaded; ensure_pyterrier_is_loaded(is_offline=False)' 

ADD baseline.py /

