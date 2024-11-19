import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import streamlit as st

# Charger le dataset
df = pd.read_excel('top_100_dishes.xlsx')

# Titre principal de l'application
st.title('Exploration des 100 Meilleurs Plats du Monde')

# Slider pour sélectionner le nombre minimum de plats par pays
min_dishes = st.slider('Nombre minimum de plats dans le top 100 par pays', 1, df['Country'].value_counts().max(), 1)

# Filtrer les pays qui ont au moins "min_dishes" plats
country_counts = df['Country'].value_counts()
filtered_countries = country_counts[country_counts >= min_dishes].index
filtered_df = df[df['Country'].isin(filtered_countries)]

# Afficher le dataset filtré
st.subheader(f'Pays avec au moins {min_dishes} plats dans le top 100')
st.write(filtered_df)

# Créer l'histogramme des plats pour les pays sélectionnés
st.subheader(f'Histogramme des pays ayant au moins {min_dishes} plats')
fig, ax = plt.subplots(figsize=(10, 6))
sns.countplot(data=filtered_df, x='Country', order=filtered_df['Country'].value_counts().index, ax=ax)
plt.xticks(rotation=90)
ax.set_title(f'Distribution des plats par pays (≥ {min_dishes} plats)')
ax.set_xlabel('Pays')
ax.set_ylabel('Nombre de plats')

# Afficher l'histogramme dans Streamlit
st.pyplot(fig)

# Afficher votre nom
def caption(name):
    st.write(f"\nCréé par {name} 😊")

caption("Arthur Gaschet")


