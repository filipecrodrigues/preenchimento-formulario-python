# 📘 Software Design Document (SDD)

## 1. Visão Geral

Automação para preencher e enviar um formulário do Google Forms com dados de uma lista de alunos, usando Python e Selenium WebDriver.

---

## 2. Objetivos

- Automatizar o preenchimento de formulários repetitivos  
- Registrar logs de sucesso ou falhas por aluno  
- Suportar múltiplas execuções com reusabilidade e facilidade de manutenção

---

## 3. Tecnologias e Ferramentas

| Tecnologia         | Finalidade                                |
|--------------------|--------------------------------------------|
| Python 3.x         | Linguagem de programação                   |
| Selenium WebDriver | Automação de navegador                     |
| ChromeDriver       | Driver para controle do navegador          |
| webdriver-manager  | Garante versão compatível do driver        |
| logging (built-in) | Registro de logs                           |
| draw.io            | Criação de diagramas de fluxo              |
| GitHub             | Versionamento de código                    |

---

## 4. Arquitetura da Solução

```
main.py
│
├── Lista de alunos (nome + CPF)
├── Navegador aberto com ChromeDriver
├── Para cada aluno:
│ ├── Acessa o formulário
│ ├── Preenche campos
│ ├── Clica em "Enviar"
│ ├── Loga resultado
│ └── Se disponível, clica em "Enviar outra resposta"
└── Fecha o navegador ao final


---

## 5. Diagrama de Fluxo

Veja o diagrama visual: `docs/fluxo_selenium.drawio.png`

---
```
## 6. Estrutura de Arquivos


preenchimento_formulario_python/
├── main.py
├── docs/
│   ├── fluxo_selenium.drawio
│   ├── fluxo_selenium.drawio.png
│   └── SDD.md
├── log_envios.txt
└── README.md




---

## 7. Tratamento de Erros

- Se campos do formulário não forem encontrados, o erro é logado  
- Se botão "Enviar outra resposta" não estiver disponível, o fluxo é encerrado  
- Qualquer exceção geral é capturada com `try/except` e registrada no log  

---

## 8. Requisitos Funcionais

1. RF01: O sistema deve abrir o formulário e preenchê-lo automaticamente  
2. RF02: Deve registrar logs para cada aluno  
3. RF03: Deve permitir múltiplas execuções sem travamentos  

---

## 9. Requisitos Não-Funcionais

1. RNF01: Código deve ser executado em navegadores com suporte ao ChromeDriver  
2. RNF02: Logs devem ser armazenados localmente em `.txt`  
3. RNF03: Tempo de execução razoável (uso de `sleep` para garantir carregamento)  

---

## 10. Considerações Finais

Esse sistema é adequado para automação simples, e pode ser expandido para:

- Suporte a arquivos `.csv`  
- Interface gráfica para importar dados  
- Integração com banco de dados  
