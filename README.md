# Ai-native-consumer-health
import streamlit as st

st.set_page_config(
    page_title="AI-Native Consumer Health",
    page_icon="🧠",
    layout="centered"
)

st.title("🧠 AI-Native Consumer Health Co-Pilot")
st.caption("AI as the interface — not a feature")

st.markdown(
    """
This experience helps consumers **understand food ingredients at the moment decisions matter**.
No ingredient lists. No filters. Just clarity.
"""
)


# INPUT

st.subheader("📦 Enter Ingredients (or use sample)")

ingredients = st.text_area(
    "Ingredients",
    placeholder="Sugar, Palm Oil, Emulsifier (E471), Artificial Flavour, Preservative",
    height=120
)

if st.button("Use Sample Ingredients"):
    ingredients = "Sugar, Palm Oil, Emulsifier (E471), Artificial Flavour, Preservative"


# AI-NATIVE REASONING (Mock)

def ai_native_reasoning(text):
    return {
        "intent": "User likely wants to know if this product is safe for regular consumption.",
        "what_matters": "The product appears highly processed and optimized for taste and shelf life.",
        "why_it_matters": "Frequent intake of ultra-processed foods is associated with digestive and metabolic concerns for some individuals.",
        "tradeoffs": "Improved flavor and convenience versus nutritional quality.",
        "uncertainty": "Scientific evidence varies between individuals and depends on consumption frequency.",
        "bottom_line": "Occasional consumption is generally fine, but it may not be ideal as a daily food choice."
    }

# OUTPUT

if st.button("🔍 Help Me Understand"):
    if not ingredients.strip():
        st.warning("Please enter ingredients or use the sample.")
    else:
        with st.spinner("AI is reasoning for you..."):
            insight = ai_native_reasoning(ingredients)

        st.subheader("🧠 What the AI Inferred")
        st.write(insight["intent"])

        st.subheader("⭐ What Actually Matters")
        st.write(insight["what_matters"])

        st.subheader("❓ Why It Matters")
        st.write(insight["why_it_matters"])

        st.subheader("⚖️ Trade-Offs")
        st.write(insight["tradeoffs"])

        st.subheader("⚠️ Uncertainty")
        st.write(insight["uncertainty"])

        st.success(f"**Bottom Line:** {insight['bottom_line']}")



st.markdown("---")
st.caption(
    "This is an AI-native experience focused on reasoning and clarity, not medical advice."
)
