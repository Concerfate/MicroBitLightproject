let meterPlaceholder = 0
let soundMeter = 0
let ifLedsOn = false
let sensorActive = false 

function lightMeterSensor() {
    if (!sensorActive) {
        sensorActive = true
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone) // Play sound when turned on
        basic.forever(function () {
            if (!sensorActive) return 
            if (input.lightLevel() < 80) {
                basic.showLeds(`
                # # # # #
                # # # # #
                # # # # #
                # # # # #
                # # # # #
                `)
                ifLedsOn = true
                soundMeter = 2
            } else {
                basic.showLeds(`
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                `)
                soundMeter = 1
                ifLedsOn = false
            }
        })
    } else {
        sensorActive = false 
        music.play(music.tonePlayable(131, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone) // Play sound when turned off
        basic.clearScreen()
    }
}

input.onButtonPressed(Button.A, function () {
    ifLedsOn = true
    soundMeter = 2
    for (let i = 0; i < 7; i++) {
        basic.showLeds(`
        # # # # #
        # # # # #
        # # # # #
        # # # # #
        # # # # #
        `)
        basic.pause(1000) 
    }
    basic.clearScreen()
    ifLedsOn = false
    soundMeter = 1
})

input.onButtonPressed(Button.B, function () {
    lightMeterSensor()
})

basic.forever(function () {
    if ((soundMeter == 1 || soundMeter == 2) && soundMeter != meterPlaceholder) {
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        meterPlaceholder = soundMeter
    }
})
