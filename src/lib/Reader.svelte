<script>
    let textToRead = ""

    const handleSubmit = () => {
        console.log("ready to read")
    }
</script>

<div class="flex flex-col items-center space-y-4 h-full w-full font-bold text-lg py-4 px-6 border-2 border-indigo-500 rounded-2xl">
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
      <div class="flex-shrink-0">
        <button type="submit" class="inline-flex items-center px-6 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">Read</button>
      </div>
    </div>
  </form>
</div>
