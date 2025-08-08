import pytest
from television import Television

def test_init():
    tv = Television()
    assert str(tv) == f"Power = False, Channel = {Television.MIN_CHANNEL}, Volume = {Television.MIN_VOLUME}"

def test_power():
    tv = Television()
    tv.power()
    assert str(tv).startswith("Power = True")
    tv.power()
    assert str(tv).startswith("Power = False")

def test_mute():
    tv = Television()
    tv.power()
    tv.volume_up()  # set volume to 1
    tv.mute()
    assert f"Volume = {Television.MIN_VOLUME}" in str(tv)  # muted volume should display 0
    tv.mute()
    assert f"Volume = 1" in str(tv)  # unmuted volume should display actual volume
    tv.power()
    tv.mute() 
    assert "Power = False" in str(tv)

def test_channel_up():
    tv = Television()
    tv.power()
    tv._Television__channel = Television.MAX_CHANNEL  # force to max channel
    tv.channel_up()
    assert f"Channel = {Television.MIN_CHANNEL}" in str(tv)

def test_channel_down():
    tv = Television()
    tv.power()
    tv._Television__channel = Television.MIN_CHANNEL  # force to min channel
    tv.channel_down()
    assert f"Channel = {Television.MAX_CHANNEL}" in str(tv)

def test_volume_up():
    tv = Television()
    tv.power()
    tv.volume_up()
    assert f"Volume = 1" in str(tv)
    tv._Television__volume = Television.MAX_VOLUME  # force to max volume
    tv.volume_up()
    assert f"Volume = {Television.MAX_VOLUME}" in str(tv)
    # test unmuting behavior
    tv._Television__muted = True
    tv.volume_up()
    assert tv._Television__muted is False

def test_volume_down():
    tv = Television()
    tv.power()
    tv._Television__volume = Television.MAX_VOLUME
    tv.volume_down()
    assert f"Volume = {Television.MAX_VOLUME - 1}" in str(tv)
    tv._Television__volume = Television.MIN_VOLUME
    tv.volume_down()
    assert f"Volume = {Television.MIN_VOLUME}" in str(tv)
    # test unmuting behavior
    tv._Television__muted = True
    tv.volume_down()
    assert tv._Television__muted is False
