# 🧪 Kali Linux Lab — Virtualização, Ambiente de Testes e Comandos Básicos

## 📌 Importância de Recuperar o Ambiente de Laboratório

Durante **testes de penetração (pentests)** é comum que sistemas sejam quebrados ou corrompidos. Isso ocorre porque o objetivo do teste é justamente explorar vulnerabilidades.

Exemplos do que pode acontecer durante testes:

- Inserção de **dados falsos em formulários**
    
- **Ataques de injeção** (SQL Injection, scripts maliciosos)
    
- **Corrupção de banco de dados**
    
- Falha de aplicações ou serviços
    
- Alteração indevida de configurações
    

Em ambientes reais (**produção**) isso pode gerar:

- perda de dados
    
- indisponibilidade de sistemas
    
- falhas de segurança
    
- impacto financeiro
    

Mesmo em **ambientes de laboratório**, isso pode causar problemas se não houver uma forma rápida de recuperação.

### Solução recomendada

Usar **virtualização**.

Ambientes virtualizados permitem:

- **Snapshots**
    
- **Rollback do sistema**
    
- Restauração rápida do ambiente
    
- Testes seguros
    

Se o sistema **não puder ser virtualizado**, é necessário manter:

- backup completo do sistema
    
- backup do banco de dados
    
- backup das configurações
    

Isso garante que o ambiente possa ser restaurado rapidamente.

---

# 🖥 Virtualização e Máquinas Virtuais

## Conceito de Virtualização

Virtualização permite executar **vários sistemas operacionais em um único computador físico**.

Elementos principais:

**Host**

- computador físico
    

**Guest (VM)**

- sistema virtual executado dentro do host
    

Exemplo:

Computador físico (Host)  
 ├── VM Kali Linux  
 ├── VM Windows  
 └── VM Ubuntu

Benefícios da virtualização:

- isolamento de ambientes
    
- facilidade de testes
    
- segurança
    
- recuperação rápida
    
- uso eficiente de hardware
    

---

# 🐉 Kali Linux

Kali Linux é uma distribuição Linux especializada em:

- **testes de penetração**
    
- **auditoria de segurança**
    
- **forense digital**
    
- **análise de vulnerabilidades**
    

Ele inclui centenas de ferramentas de segurança, como:

- scanners de vulnerabilidade
    
- ferramentas de exploração
    
- análise de rede
    
- ferramentas de engenharia social
    

⚠️ Kali não é recomendado para uso comum (como sistema principal).

---

# 🖥 Instalação da VM Kali Linux

## Requisitos mínimos

- 4 GB de RAM
    
- 50 GB de armazenamento
    
- conexão com internet
    

---

## Virtualização em computadores AMD ou Intel

Ferramenta recomendada:

**VirtualBox**

Passos principais:

1️⃣ Instalar VirtualBox  
[https://www.virtualbox.org](https://www.virtualbox.org)

2️⃣ Baixar imagem da VM Kali (arquivo `.OVA`)

3️⃣ Importar a VM

File → Import Appliance

4️⃣ Ajustar recursos da VM

- RAM
    
- CPU
    
- armazenamento
    

5️⃣ Iniciar a máquina virtual

---

## Virtualização em Macs ARM (M1/M2)

Ferramenta recomendada:

**UTM**

Passos:

1️⃣ baixar UTM  
[https://mac.getutm.app](https://mac.getutm.app)

2️⃣ baixar imagem Kali `.utm`

3️⃣ importar VM

---

# 👤 Usuário Root no Linux

No Linux existe um usuário especial chamado **root**.

Ele possui **controle total do sistema**.

Equivalente ao:

Administrador no Windows.

---

## Comando `su`

Permite trocar para usuário root.

su

Será necessário inserir a senha do root.

Para sair:

exit

---

## Comando `sudo`

Executa **apenas um comando com privilégio root**.

Exemplo:

sudo visudo

Isso permite executar o comando com privilégios elevados.

No Kali usado no laboratório:

- usuário `kali` pertence ao grupo `sudo`
    

Isso permite executar comandos administrativos.

Verificação:

grep sudo /etc/group

Resultado esperado:

sudo:x:27:kali

---

# ⌨ Atalhos importantes do Terminal

## Histórico de comandos

Comando:

history

Mostra comandos executados anteriormente.

Exemplo:

1 visudo  
2 sudo visudo  
3 grep sudo /etc/group  
4 history

---

## Executar comando do histórico

Sintaxe:

!numero

Exemplo:

!3

Executa o comando número 3.

---

Também é possível usar parte do comando:

!his

Executa:

history

---

## Autocompletar

A tecla **Tab** completa comandos automaticamente.

Exemplo:

hi + TAB

Resultado:

history

Também funciona para arquivos e diretórios.

---

# 📂 Comandos básicos de arquivos no Linux

## pwd

Mostra o diretório atual.

pwd

Exemplo:

/home/kali

---

## cd

Altera diretório.

Exemplo:

cd /home/kali

---

## ls

Lista arquivos.

ls

Versão detalhada:

ls -l

Mostra:

- permissões
    
- proprietário
    
- tamanho
    
- data
    

---

## mkdir

Cria diretórios.

Exemplo:

mkdir pasta1

Criar vários:

mkdir pasta1 pasta2 pasta3

---

# 📁 Caminhos no Linux

## Caminho absoluto

Começa da raiz `/`.

Exemplo:

/home/kali/kali_folder3

---

## Caminho relativo

Baseado no diretório atual.

Exemplo:

cd kali_folder3

---

## Diretórios especiais

`.` → diretório atual

`..` → diretório pai

`~` → diretório home do usuário

Exemplo:

cd ~

Volta para:

/home/kali

---

# 📤 Redirecionamento de saída

Operador:

>

Redireciona saída para arquivo.

Exemplo:

echo teste > arquivo.txt

Isso cria o arquivo e salva o texto.

---

## Visualizar conteúdo

cat arquivo.txt

---

## Anexar conteúdo

Operador:

>>

Exemplo:

echo novo texto >> arquivo.txt

Adiciona conteúdo **sem apagar o anterior**.

---

# ❌ Remover arquivos e diretórios

## Remover arquivo

rm arquivo.txt

---

## Remover diretório

rm -r pasta

A opção `-r` significa **recursivo**.

Remove:

- pasta
    
- arquivos internos
    
- subpastas
    

---

# 📦 Mover arquivos

Comando:

mv

Exemplo:

mv origem destino

Mover arquivo:

mv pasta1/arquivo.txt .

O `.` significa **diretório atual**.

---

Mover diretório inteiro:

mv pastaA pastaB

---

# 🖥 GUI do Kali Linux

A interface gráfica do Kali possui:

### Painel superior

Equivalente à barra de tarefas.

Contém:

- aplicativos
    
- rede
    
- áudio
    
- hora
    
- configurações
    

---

### Menu Applications

Semelhante ao **menu iniciar do Windows**.

As ferramentas são organizadas por categoria:

Exemplos:

- Information Gathering
    
- Vulnerability Analysis
    
- Web Application Analysis
    
- Wireless Attacks
    
- Exploitation Tools
    

---

# 📚 Documentação no Linux

Para acessar documentação de comandos:

man comando

Exemplo:

man ls

Isso abre o **manual completo do comando**.

---

# 💡 Reflexão: por que usar imagens pré-configuradas?

Usar uma VM Kali **pré-construída** tem várias vantagens.

### Benefícios

✔ instalação mais rápida  
✔ ambiente já configurado  
✔ ferramentas prontas para uso  
✔ menos erros de configuração  
✔ ideal para aprendizado

Se instalar manualmente:

- leva mais tempo
    
- exige configuração de dependências
    
- exige instalação de ferramentas
    

---

# 🎯 Conhecimento adquirido

Este laboratório ensina:

- uso de **virtualização para segurança**
    
- instalação de **Kali Linux**
    
- uso básico do **terminal Linux**
    
- manipulação de arquivos
    
- gerenciamento de diretórios
    
- uso de **privilégios administrativos**
    
- navegação em ambiente Linux
    

Essas habilidades são **fundamentais para pentest e cibersegurança**.