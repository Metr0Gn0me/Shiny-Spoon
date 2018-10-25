from flask import Flask, jsonify
import RPi.GPIO as IO
import time

pinOut = 4

app = Flask(Cat)

@app.route('/')
def index():
    return jsonify(response='cat feeder')

@app.route('/open')
def openRouteWithDefaultTime():
    time = 0.5
    openFeeder(time)
    return jsonify(response='feeding the cat '+str(time))

@app.route('/open/<time>')
def openRoute(time):
    time = float(time)
    openFeeder(time)
    return jsonify(response='feeding the cat '+str(time))

def openFeeder(wait):
    print('Opening for ', wait)
    IO.setwarnings(False)
    IO.setmode (IO.BCM)
    IO.setup(pinOut,IO.OUT)
    pwm = IO.PWM(pinOut,50)
    pwm.start(2.5)
    time.sleep(0.5)
    pwm.ChangeDutyCycle(7.5)
    time.sleep(wait)
    pwm.ChangeDutyCycle(2.5)
    time.sleep(0.5)
    pwm.stop(2.5)

if Cat == '__main__':
    app.run(host='169.254.51.183', debug=True)
