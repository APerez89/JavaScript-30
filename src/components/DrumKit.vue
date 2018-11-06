<template>
<div class="drumkit">
    <div class="keys">
      <div data-key="65" class="key">
        <kbd>A</kbd>
        <span class="sound">clap</span>
      </div>
      <div data-key="83" class="key">
        <kbd>S</kbd>
        <span class="sound">hihat</span>
      </div>
      <div data-key="68" class="key">
        <kbd>D</kbd>
        <span class="sound">kick</span>
      </div>
      <div data-key="70" class="key">
        <kbd>F</kbd>
        <span class="sound">openhat</span>
      </div>
      <div data-key="71" class="key">
        <kbd>G</kbd>
        <span class="sound">boom</span>
      </div>
      <div data-key="72" class="key">
        <kbd>H</kbd>
        <span class="sound">ride</span>
      </div>
      <div data-key="74" class="key">
        <kbd>J</kbd>
        <span class="sound">snare</span>
      </div>
      <div data-key="75" class="key">
        <kbd>K</kbd>
        <span class="sound">tom</span>
      </div>
      <div data-key="76" class="key">
        <kbd>L</kbd>
        <span class="sound">tink</span>
      </div>
    </div>
    <audio data-key="65" src="/dkitsound/clap.wav"></audio>
    <audio data-key="83" src="/dkitsound/hihat.wav"></audio>
    <audio data-key="68" src="/dkitsound/kick.wav"></audio>
    <audio data-key="70" src="/dkitsound/openhat.wav"></audio>
    <audio data-key="71" src="/dkitsound/boom.wav"></audio>
    <audio data-key="72" src="/dkitsound/ride.wav"></audio>
    <audio data-key="74" src="/dkitsound/snare.wav"></audio>
    <audio data-key="75" src="/dkitsound/tom.wav"></audio>
    <audio data-key="76" src="/dkitsound/tink.wav"></audio>
  </div>
</template>

<script>
export default {
  methods: {
    // eslint-disable-next-line
    playSound(e) {
      const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
      if (!audio) return; // will stop function from running

      key.classList.add('playing');
      audio.currentTime = 0; // rewind to start
      audio.play();
    },
    removeTransition(e) {
      if (e.propertyName !== 'transform') return;
      e.target.classList.remove('playing');
    },
  },
  mounted() {
    const keys = document.querySelectorAll('.key');
    keys.forEach(key => key.addEventListener('transitionend', this.removeTransition));
    window.addEventListener('keydown', this.playSound);
  },
};

</script>

<style lang="scss" scoped>
.drumkit {
  background-image: url('http://i.imgur.com/b9r5sEL.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  .keys {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    .key {
      width: 175px;
      display: flex;
      flex-direction: column;
      font-size: 50px;
      border: 4px solid #000;
      background-color: rgba(0, 0, 0, 0.6);
      margin: 0 20px;
      padding: 20px 15px;
      transition: all 0.07s;
      .sound {
        font-size: 20px;
        color: #fcc630;
      }
    }
    .playing {
      transform: scale(1.1);
      border-color: #fcc630;
      box-shadow: 0 0 10px #fcc630;
    }
  }
}
</style>
