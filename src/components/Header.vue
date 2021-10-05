<template>

  <!-- bg = background, p = padding, mb = margin bottom -->
  <header class="text-center bg-blue-800 text-white p-4 mb-10">
    <!-- md = 움직일수록 x xl 만큼 커짐 -->
    <!-- i태그 사용함 (운영체제에서 기본적으로 표현할수 없는 특수만자를 간단하게 생성) -->
    <div class="text-3xl md:text-5xl font-bold mb-3">
      <i class="fa fa-viruses"></i>Covid Tracker</div>

    <p>
      API by 
      <a class="text-blue-300" href="http://covid19api.com">covid19api.com</a>
    </p>

  </header>
</template>

<script>

export default {
  name: 'Header',
  
}
</script>

