<script>
    // helper function
    const sleep = ms => {
      return new Promise(resolve => setTimeout(resolve, ms))
    }

    let isReadingSection = false
    let readingSpeed = 300

    let textToRead = ''

    let isReading = false

    // word we are reading + index of this word
    let currentWord = ''
    let currentIndex = 0

    const onChangeSpeedValue = (e) => {
        const newValue = e.target.value
        readingSpeed = newValue.replace(/\D/g, '')
    }

    const handleReading = async () => {
        isReading = !isReading

        const timeToWait = 1000 / (readingSpeed / 60)
        const words = textToRead.split(' ')

        while (currentIndex < words.length) {
          if (!isReading) {
            break
          }

          currentWord = words[currentIndex]
          currentIndex++
          await sleep(timeToWait)
        }

        if (currentIndex === words.length) {
          currentIndex = 0
          currentWord = words[0]
        }

        isReading = false
    }

    const handleSetStart = () => {
      const words = textToRead.split(' ')

      currentIndex = 0
      currentWord = words[0]
    }

    const handleSubmit = () => {
        isReadingSection = !isReadingSection
        isReading = false
    }

    $:{
      const words = textToRead.split(' ')
      currentWord = words[0] || ''
    }
</script>

<div class="flex flex-col items-center space-y-4 h-full max-h-96 w-full font-bold text-lg py-4 px-6 border-2 border-indigo-500 rounded-2xl">
    <div class="self-start relative border border-gray-300 rounded-md px-3 py-2 shadow-sm focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
        <label for="name" class="absolute -top-2 left-2 -mt-px inline-block px-1 bg-white text-xs font-medium text-gray-900">Word Per Minute</label>
        <input
            type="text"
            name="name"
            id="speed-reading"
            bind:value={readingSpeed}
            on:input|preventDefault={onChangeSpeedValue}
            class="block w-full border-0 p-0 text-gray-900 text-right placeholder-gray-500 focus:ring-0 focus:outline-none"
            placeholder="Reading Speed">
    </div>

    {#if !isReadingSection}
        <p>Enter the text you want to fast read</p>

        <form
            class="relative h-full w-full"
            on:submit|preventDefault={handleSubmit}>
          <div class="border border-gray-300 h-full w-full rounded-lg shadow-sm overflow-hidden focus-within:border-2">
            <textarea
                bind:value={textToRead}
                autofocus
                class="h-full w-full p-4 border-0 resize-none focus:outline-0"
                placeholder="Add text to fast read..."></textarea>
          </div>

          <div class="absolute bottom-0 inset-x-0 pl-3 pr-2 py-2 flex justify-end">
            <button type="submit" class="inline-flex items-center px-6 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                Read
            </button>
          </div>
        </form>
    {:else}
        <div class="relative flex justify-center items-center border border-gray-300 h-full w-full rounded-lg shadow-sm overflow-hidden focus-within:border-2">
            <div class="flex justify-center items-center bg-red-500 w-96 h-40 my-4 rounded-lg bg-gray-300">
              <p class="text-4xl">
                {currentWord}
              </p>
            </div>
            <div class="absolute bottom-0 inset-x-0 pl-3 pr-2 py-2 flex justify-end">
                <button
                    on:click={handleSetStart}
                    class="items-center mr-4 px-6 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    Start at the beginning
                </button>
                <button
                    on:click={handleReading}
                    class="items-center mr-4 px-6 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    {isReading ? 'Pause' : 'Start'}
                </button>
                <button
                    on:click={handleSubmit}
                    class="items-center px-6 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    New Text
                </button>
            </div>
        </div>
    {/if}
</div>
