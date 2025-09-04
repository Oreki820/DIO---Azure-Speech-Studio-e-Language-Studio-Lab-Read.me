# Azure Speech & Language Studio Lab

Bem-vindo ao meu repositório do **Azure Speech Studio** e **Language Studio Lab**!  

Este projeto documenta minha experiência prática com as ferramentas avançadas da Microsoft Azure, focadas em **análise de fala e linguagem natural**, explorando como construir soluções de inteligência artificial voltadas para voz e texto.

---

## Objetivo do Desafio

O objetivo deste laboratório foi **praticar e aprofundar o uso do Azure Speech Studio e Language Studio**, desenvolvendo soluções de IA aplicadas a:

- Transformação de fala em texto e vice-versa.
- Análise de sentimentos e classificação de textos.
- Extração de entidades e detecção de idioma.

O entregável é um **repositório no GitHub** organizado com anotações, mostrando todo o processo de aprendizado.

---

## Objetivos de Aprendizagem

Após a conclusão do laboratório, adquiri habilidades para:

- Aplicar conceitos de análise de fala e linguagem natural em cenários práticos.
- Documentar processos técnicos de forma clara e estruturada.
- Utilizar o GitHub para organizar e compartilhar documentação técnica.

---

## Passo a Passo Realizado

### **1. Preparação**

1. Criei uma conta no [Microsoft Azure](https://azure.microsoft.com/pt-br/).
2. Acessei o **Azure Portal** e criei os recursos necessários:
   - **Speech Service** para análise de fala.
   - **Language Service** para análise de texto.
3. Copiei a **chave de API** e o **endpoint** de cada serviço para utilizar nos scripts.

---

### **2. Azure Speech Studio**

1. Acessei o [Azure Speech Studio](https://speech.microsoft.com/).
2. Testei a funcionalidade **Speech-to-Text**:
   - Fiz upload de arquivos `.wav` e gravei áudio direto.
   - Observei o texto gerado automaticamente.
3. Testei a funcionalidade **Text-to-Speech**:
   - Transformei textos em áudio usando vozes naturais.
   - Ajustei velocidade, tom e idioma.
4. Experimentei **Custom Speech**:
   - Treinei modelos personalizados para melhorar o reconhecimento de palavras específicas.

> Exemplo de resultado: O áudio "Olá, Azure!" foi transcrito corretamente como `"Olá, Azure!"`.

---

### **3. Azure Language Studio**

1. Acessei o [Azure Language Studio](https://language.microsoft.com/).
2. Testei **análise de sentimentos** em textos:
   - `"Estou muito feliz com este laboratório!"` → Sentimento: Positivo
   - `"Este exercício está sendo muito difícil."` → Sentimento: Negativo
3. Testei **extração de entidades**:
   - `"O evento será em São Paulo no dia 10 de setembro."` → Entidades: `São Paulo (local), 10 de setembro (data)`
4. Testei **detecção de idioma**:
   - `"Hello, how are you?"` → Idioma: Inglês
5. Testei **classificação de texto**:
   - Categorizei textos em categorias como `Educação`, `Tecnologia` e `Saúde`.
     
---

Este laboratório me permitiu:

Compreender os principais recursos do Azure Speech Studio e Language Studio.

Praticar integração com APIs de inteligência artificial.

Criar documentação organizada e clara para referência futura.

O repositório agora serve como material de estudo e guia prático para futuras implementações de soluções de IA baseadas em voz e linguagem.

---

### **4. Scripts de Exemplo**

Criei scripts Python para integrar com as APIs:

#### **Speech Studio – speech-analysis-example.py**

```python
import os
from azure.cognitiveservices.speech import SpeechConfig, SpeechRecognizer, AudioConfig

speech_key = "SUA_CHAVE_AQUI"
service_region = "SEU_ENDPOINT_AQUI"

speech_config = SpeechConfig(subscription=speech_key, region=service_region)
audio_input = AudioConfig(filename="audio_exemplo.wav")
speech_recognizer = SpeechRecognizer(speech_config=speech_config, audio_config=audio_input)

result = speech_recognizer.recognize_once()
print("Texto reconhecido:", result.text)

---

from azure.ai.textanalytics import TextAnalyticsClient
from azure.core.credentials import AzureKeyCredential

key = "SUA_CHAVE_AQUI"
endpoint = "SEU_ENDPOINT_AQUI"

client = TextAnalyticsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

documents = ["Estou muito feliz com este laboratório!"]
response = client.analyze_sentiment(documents=documents)[0]
print(f"Sentimento: {response.sentiment}")
