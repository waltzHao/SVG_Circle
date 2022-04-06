<template>
  <div class="container">
    <div>
      <p>Clockwise</p>
      <svg class="svg_clockwise">
        <circle class="svg_clockwise_circle" cx="50%" cy="50%" r="75" />
      </svg>
    </div>
    <div>
      <p>Anti-Clockwise</p>
      <svg class="svg_anti_clockwise">
        <circle class="svg_anti_clockwise_circle" cx="50%" cy="50%" r="75" />
      </svg>
    </div>
  </div>
</template>

<style scoped lang="scss">
$full_stroke-dashoffset: 471;
$stroke-dashoffset: 0;

@mixin svg {
  width: 300px;
  height: 300px;
  border-radius: 100%;
}
@mixin circle {
  fill: transparent;
  stroke-width: 150px;
  stroke-dasharray: 471;
  stroke-dashoffset: 471;
  transform: rotate(-90deg);
  transform-origin: center;
}
@mixin animation-mixin($name, $from, $to) {
  @keyframes #{$name} {
    0% {
      stroke-dashoffset: $from;
    }
    100% {
      stroke-dashoffset: $to;
    }
  }
}
@include animation-mixin(
  clock-animation,
  $full_stroke-dashoffset,
  $stroke-dashoffset
);
@include animation-mixin(
  anti-clock-animation,
  $stroke-dashoffset,
  $full_stroke-dashoffset
);
p {
  text-align: center;
  font-size: 30px;
}
.container {
  display: flex;
  justify-content: space-around;
  width: 800px;
  height: 400px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.svg_clockwise {
  @include svg;
  background: #9cc3d5ff;

  &_circle {
    @include circle;
    stroke: #0063b2ff;
    animation: clock-animation 20s linear infinite;
  }
}
.svg_anti_clockwise {
  @include svg;
  background: #adefd1ff;

  &_circle {
    @include circle;
    stroke: #00203fff;
    animation: anti-clock-animation 20s linear infinite;
  }
}
</style>