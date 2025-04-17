object RadixSort {
    fun sort(numbers: IntArray) {
        require(numbers.all { it >= 0 }) 
        var place = 1
        val maxNumber = numbers.maxOrNull() ?: return 
        repeat(maxNumber.toString().length) {
            countingSort(numbers, place)
            place *= 10
        }
    }
    private fun countingSort(numbers: IntArray, place: Int) {
        val output = IntArray(numbers.size)
        val count = IntArray(10) // Array to store digit counts

        numbers.forEach { count[getDigit(it, place)]++ }
        for (i in 1 until count.size) count[i] += count[i - 1]

        for (i in numbers.indices.reversed()) {
            val digit = getDigit(numbers[i], place)
            output[count[digit] - 1] = numbers[i]
            count[digit]--
        }
        output.copyInto(numbers) 
    }
    private fun getDigit(number: Int, place: Int) = (number / place) % 10
}
