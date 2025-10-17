# dio_bootcamp_ramsonware
Simulações educativas seguras de ransomware e keylogger — análise, detecção (YARA/Sigma), relatórios e recomendações de defesa.

O ransomware é um tipo de malware malicioso que sequestra digitalmente os dados da vítima através de criptografia avançada, tornando arquivos e sistemas inacessíveis até que um resgate seja pago. Funciona como um sequestro digital: o criminoso "tranca" os dados da vítima e exige pagamento para devolver o acesso.

Sua operação segue uma lógica precisa: primeiro, o código é desenvolvido usando algoritmos de criptografia robustos como AES-256, que geram chaves únicas para cada vítima através de geradores de números verdadeiramente aleatórios. Em seguida, o malware é distribuído principalmente através de e-mails de phishing com anexos infectados, exploração de vulnerabilidades em softwares desatualizados, downloads de software pirata ou sites comprometidos.

Uma vez executado na máquina da vítima, o ransomware inicia um processo metódico: identifica e criptografa arquivos importantes (documentos, fotos, bancos de dados), destrói as cópias originais para impossibilitar recuperação, e exibe uma mensagem de resgate com instruções de pagamento - geralmente em criptomoedas como Bitcoin para garantir anonimato.

A irreversibilidade do ataque é garantida por princípios matemáticos sólidos. A criptografia AES-256 oferece 2^256 combinações possíveis, tornando computacionalmente impossível quebrar a chave mesmo com supercomputadores - seriam necessários bilhões de anos para testar todas as possibilidades. Além disso, os criminosos utilizam criptografia assimétrica, onde apenas eles possuem a chave privada necessária para descriptografar, enquanto a vítima recebe apenas a chave pública para criptografar.

A assimetria favorece os atacantes: eles desenvolvem o código uma vez mas podem infectar milhares de vítimas, exploram uma única vulnerabilidade enquanto os defensores precisam proteger todos os pontos, e operam anonimamente através da dark web e criptomoedas. Combinado com técnicas psicológicas que criam urgência e pânico, isso torna o ransomware extremamente eficaz e lucrativo para os criminosos.

A defesa bem-sucedida requer abordagem em camadas: backups regulares e isolados (regra 3-2-1), atualizações constantes de software, treinamento de usuários para identificar phishing, segmentação de redes e sistemas de detecção precoce. A prevenção mostra-se sempre mais eficiente que a tentativa de recuperação, já que a criptografia moderna torna praticamente impossível reverter o dano sem a chave dos criminosos.
______________________________________________________________________________________________________________________________
Ransomware = Resgate + Software
É um tipo de malware que sequestra dados através de criptografia e exige pagamento para liberá-los.

Analogia do Cofre Forte:
- Seus dados = Objetos de valor dentro do cofre
- Ransomware = Troca a fechadura e tranca o cofre
- Chave de descriptografia = Única chave que abre o cofre
- Criminosos = Têm a chave e exigem resgate

- Como o Código é Criado: A Lógica por Trás
  Estrutura Básica do Ransomware
class RansomwareAvancado:
    def __init__(self):
        self.chave = self.gerar_chave_criptografia()
        self.arquivos_alvo = ['.txt', '.doc', '.pdf', '.jpg', '.xlsx']
    
    def gerar_chave_criptografia(self):
        # Gera uma chave ÚNICA e IMPREVISÍVEL
        chave_aleatoria = os.urandom(32)  # 256 bits de entropia
        return base64.urlsafe_b64encode(chave_aleatoria)


  Mecanismo de Criptografia Sólida
  def criptografar_arquivo(self, caminho_arquivo):
    # 1. Lê o arquivo original
    with open(caminho_arquivo, 'rb') as arquivo:
        dados_originais = arquivo.read()
    
    # 2. Criptografa com algoritmo forte (AES-256)
    cifra = Fernet(self.chave)
    dados_criptografados = cifra.encrypt(dados_originais)
    
    # 3. Substitui o arquivo original
    with open(caminho_arquivo + '.encrypted', 'wb') as arquivo:
        arquivo.write(dados_criptografados)
    
    # 4. DESTRÓI o arquivo original
    os.remove(caminho_arquivo)


  Como é Transmitido para a Vítima
Vetores de Infecção Comuns:
 Phishing por Email (Mais Comum - 54% dos casos)

📧 Email Aparentemente Legítimo:
De: suporte@banco.com.br
Assunto: Fatura Pendente - Ação Imediata Requerida
Anexo: fatura_urgente.pdf.exe  < (Executável disfarçado)

*POR MOTIVO DE SEGURANÇA, MUITOS DOS CODIGOS NÃO SERÃO MOSTRADOS PARA QUE NÃO SEJA POSSIVEL CRIAR O RANSONWARE*

Porque é TÃO Difícil Reverter/Quebrar
 Matemática da Criptografia Forte
Complexidade Computacional:

# AES-256: 2^256 combinações possíveis
combinacoes_possiveis = 115792089237316195423570985008687907853269984665640564039457584007913129639936

# Tempo para quebrar com computadores atuais:
computadores = 1_000_000  # 1 milhão de PCs
tentativas_por_segundo = 1_000_000_000  # 1 bilhão/s por PC
tempo_total = combinacoes_possiveis / (computadores * tentativas_por_segundo)

# Resultado: ≈ 3.67 × 10^51 ANOS  = IMPOSSÍVEL

Arquitetura Client-Server
 Fluxo de Chaves Assimétricas:

VÍTIMA (Client)                  CRIMINOSOS (Server)
     │                                  │
     ├── Gera par de chaves ───────────►│
     │   (pública + privada)            │
     │                                  │
     │◄── Criptografa chave simétrica ──┤
     │    com chave pública             │
     │                                  │
     │── Criptografa arquivos ─────────►│
     │   (usando chave simétrica)       │
     │                                  │
     │   X CHAVE PRIVADA FICA NO SERVER │
     │   > APENAS CRIMINOSOS TÊM ACESSO │

     ____________________________________________________________________________________________________________________________
     Estatísticas Alarmantes:

    Recuperação sem backup: 5-8% de sucesso

    Custo médio de recuperação: $1.85 milhões (empresas)

    Tempo médio de downtime: 23 dias

    Taxa de pagamento: 58% das vítimas pagam

     ransomware é eficaz porque explora:

    Matemática: Criptografia forte é intrinsecamente irreversível

    Psicologia: Pressão temporal e medo levam a pagamentos

    Economia: Custo/benefício favorece o criminoso

    Tecnologia: Anonimato e infraestrutura resiliente

Por isso a ênfase deve estar em:

    > Backups robustos (3-2-1 rule)

    > Educação do usuário (phishing awareness)

    > Segmentação de rede (limitar spreading)

    > Detecção precoce (monitoramento comportamental)

A compreensão desses mecanismos é o primeiro passo para construir defesas eficazes!

