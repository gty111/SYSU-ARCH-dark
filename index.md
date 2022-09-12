---
layout: default
title: Home
nav_order: 1
---

# SYSU-ARCH

{: .highlight}
> `dev`what to name exp
> 
> this is the dev version of SYSU-ARCH

SYSU-ARCH is a LAB that focus on the use and extending of simulators.

After finishing SYSU-ARCH, you will learn
- what is GEM5 and GPGPU-SIM
- the basic use of GEM5 and GPGPU-SIM
- how to extend in simulator 
- how to use simulator to research
- tools like docker and wsl

{: .highlight}
> reference [GEM5 101](https://www.gem5.org/documentation/learning_gem5/gem5_101/)(add **changes** to fit current version of GEM5 and new ideas)

<button class="btn js-toggle-dark-mode">Dark Mode</button>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Dark Mode';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Light Mode';
  }
});
</script>