from fpdf import FPDF
from datetime import datetime
from pdf2image import convert_from_path
import os

# Data tiket
judul_film = "Pengepungan di Bukit Duri"
tanggal = datetime.today().strftime('%d %B %Y')
jam_tayang = "23:00 WIB"
lokasi = "One Bell Park XXI"
studio = "Studio 3"
kursi = ["D12", "D13"]
kode_booking = ["X1B23D12", "X1B23D13"]
harga_per_tiket = "Rp60.000"
total_harga = "Rp120.000"

# Buat class PDF
class TicketPDF(FPDF):
    def header(self):
        # Logo (opsional)
        if os.path.exists("logo_xxi.png"):
            self.image("logo_xxi.png", 10, 8, 33)  # logo kiri atas
        self.set_font('Arial', 'B', 16)
        self.cell(0, 10, 'Cinema XXI - Bukti Pembayaran', ln=True, align='C')
        self.ln(10)

    def payment_receipt(self, film_title, date, time, location, studio, seats, price_per_ticket, total_price, booking_codes):
        self.set_font('Arial', '', 12)
        self.cell(40, 10, 'Judul Film:')
        self.cell(0, 10, film_title, ln=True)
        self.cell(40, 10, 'Tanggal:')
        self.cell(0, 10, date, ln=True)
        self.cell(40, 10, 'Waktu:')
        self.cell(0, 10, time, ln=True)
        self.cell(40, 10, 'Lokasi:')
        self.cell(0, 10, location, ln=True)
        self.cell(40, 10, 'Studio:')
        self.cell(0, 10, studio, ln=True)
        self.cell(40, 10, 'Jumlah Tiket:')
        self.cell(0, 10, str(len(seats)), ln=True)
        self.cell(40, 10, 'Kursi:')
        self.cell(0, 10, ', '.join(seats), ln=True)
        self.cell(40, 10, 'Harga per Tiket:')
        self.cell(0, 10, price_per_ticket, ln=True)
        self.cell(40, 10, 'Total Harga:')
        self.cell(0, 10, total_price, ln=True)
        self.cell(40, 10, 'Kode Booking:')
        self.cell(0, 10, ', '.join(booking_codes), ln=True)
        self.ln(20)
        self.set_font('Arial', 'I', 10)
        self.cell(0, 10, 'Simpan bukti ini sebagai tanda pembayaran yang sah.', ln=True)
        self.cell(0, 10, 'Terima kasih telah menonton bersama Cinema XXI.', ln=True)

# Buat PDF
pdf = TicketPDF()
pdf.add_page()
pdf.payment_receipt(judul_film, tanggal, jam_tayang, lokasi, studio, kursi, harga_per_tiket, total_harga, kode_booking)
pdf.output("Bukti_Pembayaran_Cinema_XXI.pdf")

# Konversi ke gambar PNG
images = convert_from_path("Bukti_Pembayaran_Cinema_XXI.pdf", first_page=1, last_page=1)
images[0].save("Bukti_Pembayaran_Cinema_XXI.png", "PNG")
