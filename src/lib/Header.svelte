<script>
  let isDarkMode = false;

  let toggleDarkMode = () => {
    isDarkMode = !isDarkMode
  }
</script>

<div class="w-full flex justify-between items-center">
    <h1 class="text-gray-900 text-5xl">Fast Reader</h1>

    <button type="button"
        class="{!isDarkMode ? 'bg-gray-200' : 'bg-indigo-600' } relative inline-flex flex-shrink-0 h-7 w-12 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        role="switch" aria-checked="false"
        on:click={toggleDarkMode}>
        <span
            class="{!isDarkMode ? 'translate-x-0' : 'translate-x-5' } pointer-events-none relative inline-block h-6 w-6 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200">
              <span
                  class="{!isDarkMode ? 'opacity-100 ease-in duration-200' : 'opacity-0 ease-out duration-100' } absolute inset-0 h-full w-full flex items-center justify-center transition-opacity"
                  aria-hidden="true">
                  <svg xmlns="http://www.w3.org/2000/svg"  class="h-4 w-4 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z" clip-rule="evenodd" />
                  </svg>
              </span>
              <span
                  class="{!isDarkMode ? 'opacity-0 ease-out duration-100' : 'opacity-100 ease-in duration-200'} absolute inset-0 h-full w-full flex items-center justify-center transition-opacity"
                  aria-hidden="true">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-indigo-600" fill="currentColor">
                    <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" />
                  </svg>
              </span>
        </span>
    </button>
</div>
