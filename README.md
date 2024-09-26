from flask import Flask, render_template, request
from datetime import datetime

app = Flask(__name__)

def get_zodiac_sign(day, month):
    if (month == 1 and day >= 20) or (month == 2 and day <= 18):
        return "Acuario"
    elif (month == 2 and day >= 19) or (month == 3 and day <= 20):
        return "Piscis"
    elif (month == 3 and day >= 21) or (month == 4 and day <= 19):
        return "Aries"
    elif (month == 4 and day >= 20) or (month == 5 and day <= 20):
        return "Tauro"
    elif (month == 5 and day >= 21) or (month == 6 and day <= 20):
        return "Géminis"
    elif (month == 6 and day >= 21) or (month == 7 and day <= 22):
        return "Cáncer"
    elif (month == 7 and day >= 23) or (month == 8 and day <= 22):
        return "Leo"
    elif (month == 8 and day >= 23) or (month == 9 and day <= 22):
        return "Virgo"
    elif (month == 9 and day >= 23) or (month == 10 and day <= 22):
        return "Libra"
    elif (month == 10 and day >= 23) or (month == 11 and day <= 21):
        return "Escorpio"
    elif (month == 11 and day >= 22) or (month == 12 and day <= 21):
        return "Sagitario"
    else:
        return "Capricornio"

@app.route('/', methods=['GET', 'POST'])
def index():
    sign = None
    if request.method == 'POST':
        birth_date = request.form['birth_date']
        day, month = map(int, birth_date.split('-'))
        sign = get_zodiac_sign(day, month)
    return render_template('index.html', sign=sign)

if __name__ == '__main__':
    app.run(debug=True)
