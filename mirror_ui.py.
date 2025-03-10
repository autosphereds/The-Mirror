import streamlit as st
import openai

# OpenAI API Key (You'll need to set this securely in a real deployment)
OPENAI_API_KEY = "your-api-key-here"
openai.api_key = OPENAI_API_KEY

# Sidebar navigation
st.sidebar.title("The Mirror")
page = st.sidebar.radio("Navigate", ["Consultant Dashboard", "Employee Interview", "Leadership Reports", "Data Upload", "Customization"])

if page == "Consultant Dashboard":
    st.title("Consultant Dashboard")
    st.subheader("Overview of Collected Data")
    st.write("- Access interview results\n- Identify key problem areas\n- Generate structured reports")
    st.button("Generate Report")

elif page == "Employee Interview":
    st.title("Employee Interview Interface")
    st.subheader("AI-Driven Chatbot")
    
    st.write("- Answer questions at your convenience\n- AI refines questions based on responses\n- Provides real-time feedback")
    
    if "conversation" not in st.session_state:
        st.session_state.conversation = []
    
    def get_ai_response(user_input):
        response = openai.ChatCompletion.create(
            model="gpt-4",
            messages=[
                {"role": "system", "content": "You are an AI interviewer gathering insights about workplace operations. Ask follow-up questions based on employee responses to refine your understanding of their work challenges."},
                {"role": "user", "content": user_input}
            ]
        )
        return response["choices"][0]["message"]["content"]
    
    user_input = st.text_area("Chat here...")
    if st.button("Submit Response") and user_input:
        ai_response = get_ai_response(user_input)
        st.session_state.conversation.append(("User", user_input))
        st.session_state.conversation.append(("AI", ai_response))
    
    for speaker, message in st.session_state.conversation:
        st.write(f"**{speaker}:** {message}")

elif page == "Leadership Reports":
    st.title("Leadership Reports & Insights")
    st.subheader("Key Findings & Action Plans")
    st.write("- Summarized insights from employee interviews\n- Actionable recommendations\n- Interactive data visualization")
    st.button("Download Report")

elif page == "Data Upload":
    st.title("Upload Business Data")
    st.subheader("File Upload & Initial Data Feeding")
    uploaded_file = st.file_uploader("Upload Report File", type=["csv", "xlsx", "pdf"])
    if uploaded_file:
        st.success("File uploaded successfully!")

elif page == "Customization":
    st.title("Customization Panel")
    st.subheader("Tailor The Mirror to Business Needs")
    st.write("- Define business-specific interview paths\n- Adjust KPIs & benchmarks\n- Configure dashboard settings")
    st.button("Save Changes")
