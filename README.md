# TYDAC
From the book

```
>>> import board
>>> import busio
>>> i2c = busio.I2C(board.GP1, board.GP0)
>>> i2c.try_lock()
True
>>> i2c.scan()
[112]
>>> ADDR = 0x70 # 112
>>> i2c.writeto(ADDR, bytes([0x21]) ) # 0010_xxx1 Turn the oscillator on
>>> i2c.writeto(ADDR, bytes([239]) ) # 1110_1111 Full brightness
>>> i2c.writeto(ADDR, bytes([0b10000001]) ) # 1000_x001 Blinking off, display on
>>> i2c.writeto(ADDR, bytes([0, 255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255]) )
```