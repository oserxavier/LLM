# 📝 Sumarizador de Artigos com LLM, LangChain e Streamlit

Este projeto consiste em uma aplicação web interativa desenvolvida com **Streamlit**, integrando um modelo de linguagem natural (LLM) via **LangChain**, com o objetivo de gerar resumos automáticos de textos extensos. O sistema permite ao usuário colar ou carregar um texto e receber instantaneamente um resumo claro e objetivo.

## 🔍 Objetivo

Criar uma solução prática baseada em NLP (Natural Language Processing) que:

- Utilize uma LLM (ex: GPT-3.5-turbo) para processar textos.
- Aplique técnicas de prompt engineering para obter resumos consistentes.
- Ofereça uma interface amigável e intuitiva com Streamlit.
- Demonstre integração de componentes com o framework LangChain.

---

## ⚙️ Tecnologias Utilizadas

- **Python 3.10+**
- **Streamlit** – Interface web interativa
- **LangChain** – Framework para orquestração de LLMs
- **OpenAI GPT-3.5-turbo** – Modelo de linguagem para sumarização
- **PromptTemplate / LLMChain** – Componentes LangChain
- **Secrets API** – Armazenamento seguro da chave de API OpenAI

---

## 🧱 Estrutura da Aplicação

1. **Entrada do usuário:**  
   O usuário insere o texto manualmente por meio de um campo de texto.

2. **Construção do prompt:**  
   Um template personalizado instrui o modelo a gerar um resumo informativo e direto.

3. **Processamento via LangChain:**  
   A chain (`LLMChain`) envia o texto e o prompt para a LLM e obtém a resposta.

4. **Resposta:**  
   O resumo é exibido em tempo real na interface, pronto para ser copiado ou utilizado.

---

## 📄 Exemplo de Código

```python
from langchain.chat_models import ChatOpenAI
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate

prompt = PromptTemplate(
    input_variables=["conteudo"],
    template="""
    Resuma o texto abaixo de forma clara e objetiva, mantendo os pontos principais:

    Texto: {conteudo}

    Resumo:
    """
)

llm = ChatOpenAI(temperature=0.3, model_name="gpt-3.5-turbo")
chain = LLMChain(llm=llm, prompt=prompt)
