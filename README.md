# 📄 Estudos e Simulações de Ransomware e Keylogger com Python

## 🔍 Introdução

Este projeto reúne meus estudos sobre o funcionamento interno de dois tipos de malware bastante conhecidos: ransomware e keylogger. Meu objetivo foi compreender como essas ameaças são estruturadas, quais técnicas utilizam, como operam na prática e quais estratégias ajudam a preveni-las. Toda a investigação foi feita explorando conceitos, analisando comportamentos comuns e simulando as lógicas apresentadas, utilizando Python como ferramenta base para experimentação.

---

## 🦠 1. Ransomware — Estrutura, Lógica e Funcionamento

Durante meus estudos, busquei entender o fluxo de funcionamento de um ransomware desde o primeiro até o último passo. A essência desse tipo de ataque é relativamente simples, mas extremamente eficaz quando executada de forma maliciosa.

### ✔️ 1.1 Como um ransomware opera

O ciclo básico de um ransomware segue uma sequência lógica:

**1 — Identificação dos arquivos:**  
O malware escolhe quais arquivos serão “sequestrados”, normalmente por extensão ou diretórios específicos.

**2 — Leitura e captura do conteúdo:**  
Os dados do arquivo são carregados em memória.

**3 — Criptografia:**  
O conteúdo é transformado em algo ilegível usando alguma chave.  
Aqui, o ponto fundamental é a irreversibilidade sem essa chave.

**4 — Exclusão do arquivo original:**  
O arquivo legítimo é substituído ou apagado.

**5 — Criação da versão criptografada:**  
Um novo arquivo surge no lugar do antigo, agora inacessível pelo usuário.

**6 — Mensagem de bloqueio:**  
Surge a notificação informando que os dados foram bloqueados.

Esse fluxo é direto, mas conecta conceitos importantes: manipulação de arquivos, criptografia, lógica de substituição e ciclo de escrita.

### ✔️ 1.2 O que aprofundei no estudo sobre ransomware

- Como arquivos são lidos, apagados e recriados por scripts.  
- Como a criptografia se encaixa nesse processo e por que torna o ataque tão poderoso.  
- Como um ataque pode escalar rapidamente quando aplicado em múltiplos arquivos.  
- O papel da “chave” na reversão do processo.  
- Por que usuários ficam completamente dependentes do atacante nesses casos.

Também explorei exemplos comuns de como as vítimas acabam se infectando:

**• Exemplos de como usuários caem em ransomware**

- anexos falsos enviados por e-mail  
- instaladores de programas piratas  
- atualizações falsas de navegador  
- arquivos disfarçados em plataformas de mensagens  
- anúncios que redirecionam para downloads suspeitos  
- macros maliciosas em documentos de escritório

Entendi que o ponto central de ataques desse tipo é uma mistura de ingenuidade, descuido e engenharia social.

---

## ⌨️ 2. Keylogger — Captura, Armazenamento e Técnicas de Ocultação

Após compreender ransomware, avancei para o estudo dos keyloggers. A base desse tipo de malware é diferente: em vez de sequestrar arquivos, ele se concentra em registrar tudo que o usuário digita.

### ✔️ 2.1 Entendendo a lógica de um keylogger

O fluxo geral de um keylogger segue três etapas principais:

**1 — Captura de teclas:**  
Monitora eventos do teclado e registra cada tecla pressionada.

**2 — Armazenamento:**  
As informações são organizadas normalmente em um arquivo de texto.

**3 — Encaminhamento dos dados (em ataques reais):**  
Os registros podem ser enviados periodicamente para outro dispositivo ou servidor.

### ✔️ 2.2 O que analisei sobre keylogger

Durante o estudo, explorei conceitos importantes:

**• Captura de eventos**  
Como programas conseguem monitorar teclas presas ou soltas, independentemente da janela ativa.

**• Registro estruturado**  
A importância de organizar logs para que os dados capturados façam sentido.

**• Ocultação (stealth)**  
Uma das características mais fortes de keyloggers é a capacidade de permanecerem invisíveis ao usuário.  
Em estudos conceituais, entendi como isso pode ser feito através de:

- execução sem janelas  
- nomes de processos que parecem legítimos  
- início automático junto com o sistema  
- funcionamento silencioso em segundo plano  

**• Comunicação remota**

Durante os estudos, também aprendi como um keylogger pode enviar as informações capturadas para outra máquina. Essa etapa é fundamental para entender como esses programas conseguem repassar dados ao atacante sem que o usuário perceba.

Para isso, usei duas bibliotecas do Python:

- `email`, para montar a mensagem e anexar o arquivo de log gerado pelo keylogger;  
- `smtplib`, para fazer a conexão com o servidor de e-mail e realizar o envio.

O funcionamento ficou bem simples de entender:

- o keylogger registrava as teclas em um arquivo `.txt`;  
- o script montava uma mensagem usando a biblioteca `email`;  
- através do `smtplib`, ele se conectava ao servidor e enviava o arquivo para a conta configurada.

Isso me ajudou a visualizar como um malware consegue transmitir informações para outra pessoa de forma silenciosa, usando ferramentas totalmente comuns. Mesmo sendo uma simulação, deu pra entender claramente o conceito de envio remoto e como esse tipo de comunicação é utilizada em ataques reais.

### ✔️ 2.3 Como as pessoas caem em keyloggers

Ao pesquisar casos reais, notei que keyloggers são instalados de forma muito semelhante aos ransomwares, principalmente por:

- instaladores falsos  
- cracks, cheats e ativadores  
- extensões de navegador fraudulentas  
- apps “úteis” que escondem código malicioso  
- campanhas de phishing  
- programas supostamente “gratuitos” com funções extras  

O usuário normalmente não percebe nada, porque o keylogger não interfere visivelmente no funcionamento do computador.

---

## 🛡️ 3. Estratégias de Defesa

Compreender o funcionamento das ameaças facilitou visualizar como se proteger delas. Anotei as principais defesas eficazes:

### ✔️ Antivírus e ferramentas de detecção  
Identificam padrões de comportamento anormal, como tentativas de criptografia em massa ou monitoramento de teclado.

### ✔️ Firewall  
Bloqueia comunicações externas indesejadas, impedindo exfiltração de dados.

### ✔️ Atualizações constantes  
Falhas antigas são portas de entrada para vários ataques automatizados.

### ✔️ Conscientização e comportamento  
O ponto mais crítico. A maioria dos ataques depende do clique do usuário.

### ✔️ Backups  
A forma mais importante de anular o impacto de um ransomware.

---

## 📘 Conclusão

Estudar os conceitos de ransomware e keylogger me permitiu entender com profundidade como esses malwares exploram tanto falhas técnicas quanto comportamentais. Aprendi como operam, quais etapas compõem seus fluxos, como se tornam eficazes e de que forma podem capturar ou bloquear dados.

Também pude observar padrões de invasão, identificar mecanismos comuns de propagação e reconhecer práticas essenciais de defesa. Este trabalho representa a consolidação desse estudo e meu primeiro passo na compreensão prática de ameaças digitais e fundamentos de cibersegurança.
