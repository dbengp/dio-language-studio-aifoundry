# dio-language-studio-aifoundry
Resumo dos passos para se usar o poder da Análise de Sentimentos com Language Studio no Azure AI dentro do contexto de uma plataforma de Cursos com a DIO (combinação de cursos de TI e seleção de vagas, com um ranking baseado em contribuições técnicas).

1. Azure Speech Studio:
- Transcrição e Análise de Conteúdo de Vídeo:
  - Transcreva automaticamente os vídeos de tutoriais e explicações de tecnologias, gerando legendas e facilitando a busca por conteúdo específico.
  - Analise o conteúdo transcrito para identificar os tópicos mais abordados, a clareza das explicações e o engajamento do público.
  - Utilize a análise de sentimento para avaliar a receptividade dos espectadores em relação aos vídeos.
- Acessibilidade e Tradução:
  - Gere legendas e traduções automáticas para os vídeos, tornando o conteúdo acessível a um público global.
  - Ofereça a opção de narração automática para os materiais de estudo, auxiliando alunos com dificuldades de leitura.
- Interação por Voz em Bots e Aplicativos:
  - Implemente interfaces de voz em seus bots e aplicativos, permitindo que os usuários interajam com a plataforma por meio de comandos de voz.
  - Crie assistentes virtuais que respondem a perguntas sobre cursos, vagas e processos de seleção.

2. Azure Language Studio:
- Análise de Texto e Ranqueamento de Conteúdo:
  - Analise os artigos e descrições de projetos publicados pelos usuários para identificar os tópicos abordados, a complexidade técnica e a qualidade da escrita.
  - Utilize a análise de sentimento para avaliar o tom e a receptividade dos comentários e discussões.
  - Implemente um sistema de ranqueamento automático que considera a relevância, a qualidade e o engajamento do conteúdo.
- Extração de Informações e Correspondência de Vagas:
  - Extraia informações relevantes de currículos e perfis de candidatos, como habilidades, experiência e formação.
  - Utilize a correspondência de entidades para identificar as tecnologias e habilidades mais demandadas pelas empresas.
  - Crie um sistema de recomendação de vagas que considera o perfil dos candidatos e as exigências das empresas.

3. Criação de Bots e Assistentes Virtuais:
  - Desenvolva bots e assistentes virtuais que respondem a perguntas sobre cursos, vagas, processos de seleção e informações sobre a plataforma.
  - Utilize o reconhecimento de intenções para entender as necessidades dos usuários e fornecer respostas personalizadas.
  - Forneça a opção de tradução de textos, para que os usuários possam acessar conteudo em outros idiomas.
  - Um bot que responde a perguntas sobre os cursos disponíveis, como "Qual o curso mais indicado para quem quer aprender Python para análise de dados?".
  - Um sistema de recomendação de vagas que sugere oportunidades de emprego com base nas habilidades e experiências do candidato.
  - Um sistema de ranqueamento de conteúdo que destaca os artigos e vídeos mais relevantes e populares da plataforma.
 
Ao integrar esses serviços de IA do Azure, você pode criar uma plataforma de cursos e seleção de TI mais inteligente, eficiente e personalizada, oferecendo uma experiência superior aos seus usuários e impulsionando o crescimento do seu negócio.

Implementando Azure Speech Studio e Language Studio com SDKs:
Para integrar os serviços do Azure Speech Studio e Language Studio de forma programática em sua plataforma de cursos e seleção de TI, você utilizará os SDKs oficiais fornecidos pela Microsoft. Abaixo, detalho os passos necessários para cada serviço:

1. Configuração Inicial:
  - Conta Azure e Recurso de Serviços Cognitivos:
  - Como mencionado anteriormente, crie uma conta Azure e um recurso de Serviços Cognitivos no portal do Azure.
  - Anote as chaves de acesso e o endpoint.
  - Instalação dos SDKs:
  - Dependendo da linguagem de programação que você utiliza (Python, .NET, Java, etc.), instale os SDKs correspondentes. Por exemplo, para Python:
  ```
      pip install azure-cognitiveservices-speech
      pip install azure-ai-textanalytics
  ```
2. Integração do Azure Speech Studio com SDK:
  - Transcrição de Vídeos (Speech to Text):
      - Importe as bibliotecas necessárias:
      ```
          import azure.cognitiveservices.speech as speechsdk
      ```
      - Crie uma configuração de reconhecimento de fala:
      ```
         speech_config = speechsdk.SpeechConfig(subscription="CHAVE", region="REGIAO")
      ```
      - Configure a entrada de áudio (a partir de um arquivo, por exemplo):
      ```
         audio_input = speechsdk.AudioConfig(filename="seu_video.wav")
      ```
      - Crie um reconhecedor de fala:
      ```
        speech_recognizer = speechsdk.SpeechRecognizer(speech_config=speech_config, audio_config=audio_input)
      ```
      - Realize a transcrição:
      ```
        result = speech_recognizer.recognize_once_async().get()
        print(result.text)
      ```

  - Texto para fala (Text to Speech):
      - Importe as bibliotecas necessárias:
      - import azure.cognitiveservices.speech as speechsdk
      - Crie uma configuração de fala:
      ```
        speech_config = speechsdk.SpeechConfig(subscription="SUA_CHAVE", region="SUA_REGIAO")
      ```
      - Configure a saida de audio:
      ```
        audio_config = speechsdk.audio.AudioOutputConfig(use_default_speaker=True)
      ```
      - Crie um sintetizador de fala:
      ```
        synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config, audio_config=audio_config)
      ```
      - Sintetize a fala:
      ```
        synthesizer.speak_text_async("Texto para ser falado")
      ```

3. Integração do Azure Language Studio com SDK:
  - Análise de Texto (Text Analytics):
      - Importe as bibliotecas necessárias:
      ```
        from azure.core.credentials import AzureKeyCredential
        from azure.ai.textanalytics import TextAnalyticsClient
      ```
      - Crie um cliente de análise de texto:
      ```
        credential = AzureKeyCredential("SUA_CHAVE")
        text_analytics_client = TextAnalyticsClient(endpoint="SEU_ENDPOINT", credential=credential)
      ```
      - Realize a análise de sentimento:
      ```
        documents = ["Texto para análise"]
        response = text_analytics_client.analyze_sentiment(documents=documents)[0]
        print(response.sentiment)
      ```
      - Realize a extração de entidades:
      ```
        response = text_analytics_client.recognize_entities(documents = documents)[0]
        for entity in response.entities:
        print(entity.text)
      ```

4. Explore a documentação oficial dos SDKs para conhecer todas as funcionalidades disponíveis e os parâmetros de configuração. Nesse repositório <https://github.com/Azure-Samples> é possível obter informações e codificação sobre diversos usos de recursos dos serviços tanto de IA quanto outros do Azure.
