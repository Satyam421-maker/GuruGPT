
import streamlit as st
from langchain_community.chat_models import ChatOpenAI
from langchain.schema import HumanMessage
import os

# Set OpenRouter API key and base URL
os.environ["OPENAI_API_KEY"] = "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"
os.environ["OPENAI_API_BASE"] = "https://openrouter.ai/api/v1"

st.set_page_config(page_title="🕉️ GuruGPT", layout="centered")
st.title("🧘 GuruGPT")
st.markdown("Ask questions in **Hindi**, **English**, or **Sanskrit**. Receive AI wisdom and even Shlokas ✨")

question = st.text_area("🗣️ Enter your question to GuruGPT")
language = st.radio("🌐 Choose Language", ["English", "Hindi", "Sanskrit"])

if st.button("Ask GuruGPT"):
    if question.strip() == "":
        st.warning("Please enter a question first.")
    else:
        llm = ChatOpenAI(model_name="openai/gpt-3.5-turbo", temperature=0.7)

        if language == "Hindi":
            prompt = f"इस प्रश्न का उत्तर हिंदी में दीजिए:
{question}"
        elif language == "Sanskrit":
            prompt = f"Please explain in Sanskrit and include a relevant shloka if possible:
{question}"
        else:
            prompt = question

        response = llm([HumanMessage(content=prompt)])
        st.markdown("### 🧠 GuruGPT says:")
        st.success(response.content)
