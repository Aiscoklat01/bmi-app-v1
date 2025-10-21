import streamlit as st
import matplotlib.pyplot as plt

# Senarai makanan dan kalori
makanan_kalori = {
    'Nasi': 130,
    'Ayam Goreng': 240,
    'Sayur Broccoli': 35,
    'Ikan Bakar': 180,
    'Telur Rebus': 155,
    'Air Sirap': 50,
    'Mi Sup': 150,
    'Keoteow Sup': 200,
    'Maggi Sup': 250,
    'Burger Benjo': 300,
    'Wedges': 250,
    'Mi Goreng': 200,
    'Nasi Goreng': 250,
    'Sosej': 300,
    'Donut': 400,
    'Popia Goreng': 250,
    'Kuih Lapis': 150,
    'Sagu Merah': 100,
    'Sambal': 100,
    'Air Mineral': 0,
    'Keropok Lekor': 300,
    'Wrap Ayam': 350,
}

def kira_bmi(berat, tinggi_cm):
    tinggi_m = tinggi_cm / 100
    bmi = berat / (tinggi_m * tinggi_m)
    return bmi

def kategori_bmi(bmi):
    if bmi < 18.5:
        return "Kekurangan berat badan"
    elif bmi < 25:
        return "Normal"
    elif bmi < 30:
        return "Berat berlebihan"
    else:
        return "Obes"

def kira_kalori(berat, tinggi_cm, umur, jantina, tahap_aktiviti):
    if jantina == "Lelaki":
        bmr = 10 * berat + 6.25 * tinggi_cm - 5 * umur + 5
    else:
        bmr = 10 * berat + 6.25 * tinggi_cm - 5 * umur - 161

    faktor_aktiviti = {
        "Sedentari": 1.2,
        "Ringan": 1.375,
        "Sederhana": 1.55,
        "Aktif": 1.725,
        "Sangat Aktif": 1.9
    }
    return bmr * faktor_aktiviti[tahap_aktiviti]

st.title("Kalkulator BMI dan Kalori")

pilihan = st.selectbox("Pilih fungsi:", ["Kalkulator BMI", "Kalkulator Kalori"])

if pilihan == "Kalkulator BMI":
    berat = st.number_input("Berat badan (kg)", min_value=1.0, value=70.0)
    tinggi = st.number_input("Tinggi badan (cm)", min_value=30.0, value=170.0)

    if st.button("Kira BMI"):
        bmi = kira_bmi(berat, tinggi)
        kategori = kategori_bmi(bmi)
        st.write(f"BMI anda ialah: {bmi:.2f}")
        st.write(f"Kategori: {kategori}")

else:
    st.header("Kira Kalori Makanan")
    makanan_pilihan = st.multiselect("Pilih makanan:", list(makanan_kalori.keys()))
    jumlah_pilihan = st.number_input("Jumlah makanan (dalam unit):", min_value=1, value=1)

    if st.button("Kira Kalori"):
        total_kalori = sum(makanan_kalori[makanan] * jumlah_pilihan for makanan in makanan_pilihan)
        st.write(f"Jumlah kalori yang diambil: {total_kalori} kcal")

        # Carta Silang Pangkah
        kalori_makanan = {makanan: makanan_kalori[makanan] * jumlah_pilihan for makanan in makanan_pilihan}
        st.bar_chart(kalori_makanan)

    st.write("Senarai makanan dan kalori:")
    for makanan, kalori in makanan_kalori.items():
        st.write(f"{makanan}: {kalori} kcal")
