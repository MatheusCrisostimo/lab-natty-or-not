# Natural ou Fake Natty? Como Vencer na Era das IAs Generativas

## 🚀 Introdução

> Woooow! Look at this 👀

Olá pessoal, Venilton da DIO aqui! Inspirado na hype _"Natty or Not"_ do fisiculturismo, este Lab da DIO te convida a conhecer o mundo das IAs Generativas, explorando o potencial dessas tendências tecnológicas incríveis!

## 🎯 Bora Pro Desafio!? Você Já Venceu 💪🤓

### Objetivos

1. **Explorar IAs Generativas**: Utilize essas tecnologias para criar conteúdos que sejam o mais realista possível. Seja criativo! Você pode produzir imagens, textos, áudios, vídeos ou combinações de tudo isso!
1. **Potfólio de Projetos**:
    1. Faça o "fork" deste repositório, criando uma cópia em seu GitHub pessoal;
    2. Edite seu README com os detalhes do seu projeto, siga nosso [Template](#template) (é só copiar, colar e preencher);
    3. Submeta o link do seu repositório na plataforma da DIO. Pronto, você acabou de fortalecer seu portfólio de projetos nos perfis do GitHub e DIO 🚀
1. **Efeito de Rede**: Compartilhe seus resultados nas redes sociais com a hashtag **#LabDIONattyOrNot**. Não esqueça de nos marcar: [DIO](https://www.linkedin.com/school/dio-makethechange) e [falvojr](https://www.linkedin.com/in/falvojr).

### Template

```markdown
# Título do Projeto: Podcast Automatizado com Vozes Sintéticas 😉
## 📒 Descrição
Este projeto cria um podcast automatizado onde scripts, vozes e efeitos sonoros são gerados por IA. Cada episódio é criado e publicado automaticamente, proporcionando uma experiência auditiva única e inovadora.

## 🤖 Tecnologias Utilizadas
GPT-4: Utilizado para a geração de scripts de alta qualidade com base em temas específicos.
Google's Text-to-Speech: Empregado para sintetizar vozes realistas e naturais a partir dos scripts gerados.
PyDub: Utilizado para a edição de áudio e adição de efeitos sonoros.
Requests: Utilizado para publicar os episódios automaticamente em plataformas de podcast.

## 🧐 Processo de Criação
Descrevemos abaixo como cada parte do processo é implementada usando Python.

Arquivo: main.py
python
Copiar código
import generate_script
import synthesize_voice
import add_sound_effects
import publish_podcast

def main():
    # Passo 1: Gerar o script
    script = generate_script.create_script(theme="Tecnologia e IA")
    
    # Passo 2: Sintetizar a voz
    audio_path = synthesize_voice.create_voice(script)
    
    # Passo 3: Adicionar efeitos sonoros
    final_audio = add_sound_effects.add_effects(audio_path)
    
    # Passo 4: Publicar o podcast
    publish_podcast.publish(final_audio)

if __name__ == "__main__":
    main()
Arquivo: generate_script.py
python
Copiar código
import openai

def create_script(theme):
    openai.api_key = 'YOUR_OPENAI_API_KEY'
    
    prompt = f"Crie um script de podcast sobre {theme}."
    
    response = openai.Completion.create(
        engine="gpt-4",
        prompt=prompt,
        max_tokens=1000
    )
    
    script = response.choices[0].text.strip()
    return script
Arquivo: synthesize_voice.py
python
Copiar código
from google.cloud import texttospeech

def create_voice(script):
    client = texttospeech.TextToSpeechClient()

    synthesis_input = texttospeech.SynthesisInput(text=script)
    
    voice = texttospeech.VoiceSelectionParams(
        language_code="en-US",
        ssml_gender=texttospeech.SsmlVoiceGender.NEUTRAL
    )
    
    audio_config = texttospeech.AudioConfig(
        audio_encoding=texttospeech.AudioEncoding.MP3
    )
    
    response = client.synthesize_speech(
        input=synthesis_input, 
        voice=voice, 
        audio_config=audio_config
    )

    audio_path = "output.mp3"
    with open(audio_path, "wb") as out:
        out.write(response.audio_content)
    
    return audio_path
Arquivo: add_sound_effects.py
python
Copiar código
from pydub import AudioSegment

def add_effects(audio_path):
    audio = AudioSegment.from_mp3(audio_path)
    
    # Exemplo de adição de um efeito sonoro
    sound_effect = AudioSegment.from_file("path/to/sound_effect.wav")
    combined = audio.overlay(sound_effect, position=1000)
    
    final_audio_path = "final_output.mp3"
    combined.export(final_audio_path, format="mp3")
    
    return final_audio_path
Arquivo: publish_podcast.py
python
Copiar código
import requests

def publish(audio_path):
    url = "YOUR_PODCAST_HOSTING_API_ENDPOINT"
    headers = {
        'Authorization': 'Bearer YOUR_API_KEY'
    }
    
    with open(audio_path, 'rb') as audio_file:
        files = {
            'file': audio_file
        }
        response = requests.post(url, headers=headers, files=files)
    
    if response.status_code == 201:
        print("Podcast publicado com sucesso!")
    else:
        print("Falha ao publicar o podcast.", response.text)
## 🚀 Resultados
O projeto resultou na criação de vários episódios de podcast, cada um com temas distintos e interessantes, narrados por vozes sintéticas realistas e enriquecidos com efeitos sonoros. Esses episódios foram publicados automaticamente, demonstrando a eficiência e a capacidade das tecnologias de IA em automatizar a produção de conteúdo de alta qualidade.

## 💭 Reflexão (Opcional)
Criar este podcast automatizado foi um desafio intrigante, especialmente na integração das diferentes tecnologias de IA. A experiência destacou o potencial incrível dessas ferramentas para transformar a criação de conteúdo digital, permitindo a produção de material 'natty' (natural) e envolvente com mínima intervenção humana. A curva de aprendizado foi significativa, mas os resultados provaram ser recompensadores e abriram novas possibilidades para futuros projetos baseados em IA.
```

### Exemplos e Insigths

- [E-BOOK](/exemplos/E-BOOK.md)
- [Podcast](/exemplos/PODCAST.md)
- [Vídeo (Avatar Virtual)](/exemplos/VIDEO.md)

## Links Interessantes

[Base10: If You’re Not First, You’re Last: How AI Becomes Mission Critical](https://base10.vc/post/generative-ai-mission-critical/)

![Base10's Trend Map Generative AI](https://github.com/digitalinnovationone/lab-natty-or-not/assets/730492/f4df26e8-f8f7-4419-8252-c69d73ea930c)
