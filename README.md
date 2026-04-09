from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def home():
    return '''
        <h1>Form Sederhana</h1>
        <form method="POST" action="/hasil">
            Nama: <input type="text" name="nama"><br><br>
            Umur: <input type="number" name="umur"><br><br>
            <button type="submit">Kirim</button>
        </form>
    '''

@app.route('/hasil', methods=['POST'])
def hasil():
    nama = request.form.get('nama')
    umur = request.form.get('umur')
    return f"Halo {nama}, umur kamu {umur} tahun"

if __name__ == '__main__':
    app.run(debug=True)
