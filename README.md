
import streamlit as st

st.set_page_config(
    page_title="CodeFix-AI",
    page_icon="🤖"
)

st.title("🤖 CodeFix-AI")
st.subheader("Your Personal Coding Assistant")

st.write(
    "Find coding errors and understand "
    "them in simple English."
)

st.divider()

st.header("Enter Your Python Code")

code = st.text_area(
    "Paste your Python code here:",
    height=200,
    placeholder="print('Hello World')"
)

if st.button("Check Code"):

    if code.strip() == "":
        st.warning("Please enter some Python code.")

    else:
        try:
            compile(code, "<string>", "exec")
            st.success("No syntax errors found! 🎉")

        except SyntaxError as error:
            st.error("Syntax Error Found!")
            st.write("Error:", error.msg)
            st.write("Line Number:", error.lineno)

st.divider()

st.caption("Developed by Sudarshana | CodeFix-AI")
