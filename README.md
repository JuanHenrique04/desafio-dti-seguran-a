<img alt="gif" width="150" src="https://steamuserimages-a.akamaihd.net/ugc/960838399170225866/21D9841F8E03ED30D91A7720388E1E8D3A464FC0/?imw=5000&imh=5000&ima=fit&impolicy=Letterbox&imcolor=%23000000&letterbox=false">

# Desafio-dti-seguranca

# Relatório de Teste de Penetração

## 1. Resumo Executivo
- **Data do Teste:** 19/09/2024
- **Responsável:** Juan Henrique
- **Escopo do Teste:** Arquivos PDF fornecidos pela equipe de segurança para teste.
- **Objetivo:** Acessar arquivos PDF protegidos e capturar a flag
- **Conclusão:** Flag adquirida: {v0c3_3nc0ntr0u_4_fl4g}

## 2. Introdução
- **Descrição do Pentest:** O teste foi solicitado para nivelar o nível de conhecimento.
- **Ferramentas Utilizadas:** [OS Kali Linux](https://www.kali.org/) e [John the Ripper](https://www.kali.org/tools/john/)

## 3. Escopo do Teste
- **Arquivos Testados:** Desafio_de_seguranca.pdf e Desafio_de_seguranca_2.pdf
- **Ambiente:** Ambiente de testes controlado em VM (Virtual Box)

## 4. Metodologia
- **Fases do Pentest:** 
  1. **Coleta dos arquivos PDF protegidos.** 
  2. **Preparação dos arquivos para análise com John the Ripper.**
  3. **Execução da ferramenta John the Ripper para quebra das senhas.**
  4. **Análise dos resultados**
  5. **Pós-Exploração (Post-Exploitation):**
     - Acesso obtido, dados críticos acessados, movimentação lateral, etc.
  6. **Relatório (Reporting):**
     - Consolidação dos resultados

## 5. Procedimentos
#### 5.1. Coleta dos Arquivos: Os arquivos foram recebidos e inseridos no ambiente de teste (Kali Linux) para utilizar das ferramentas que o sistema disponibiliza.
#### 5.2. Preparação dos arquivos para análise com John the Ripper: Para analisar a senha do arquivo, precisamos obter o hash da senha desse arquivo. Para isso, utilizamos a ferramenta pdf2john do John the Ripper e direcionamos a saída dos arquivos para outro arquivo     .txt, que conterá o hash.
~~~bash
pdf2john Desafio_de_seguranca.pdf Desafio_de_seguranca_2.pdf > hashs.txt
~~~
#### 5.3. Execução da ferramenta John the Ripper para quebra das senhas: Após obter o hash da senha dos arquivos, podemos utilizar o John para realizar um ataque de Brute Force (Força Bruta) para encontrarmos a senha do arquivo. Nesta fase, o ataque de Brute Force usará uma wordlist (arquivo com uma lista de possíveis senhas) e irá transformar e comparar o hash de cada uma para validar qual é a senha.
~~~bash
john hashs.txt --wordlist=/usr/share/wordlists/rockyou.txt
~~~
#### 5.4. Análise dos resultados: Após a execução da ferramenta, obtivemos a senha dos 2 arquivos PDF protegidos ->
Desafio_de_seguranca.pdf = 1234;
<br>
<img alt="arq1" width="500" src="https://github.com/user-attachments/assets/81db5c83-ef3a-477c-b7a4-0997bb010bf5">

<br>
Desafio_de_seguranca_2.pdf = bubblegum.
<br>
<img alt="arq2" width="500" src="https://github.com/user-attachments/assets/8f9a95c4-b96d-4334-9d83-e398ea78e500">

## 6. Relatório
- Senhas simples e comuns em arquivos PDF são vulneráveis e podem ser quebradas facilmente usando ferramentas de força bruta.
- Arquivos PDF com proteção mais robusta são menos suscetíveis à quebra rápida, mas ainda podem ser vulneráveis a ataques mais sofisticados.
