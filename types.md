Q. Given an integer, determine if it is a power of four. Do not use built-in functions or operators to solve this problem.

A.
function solution(num: number): boolean {
    if(num <= 0) return false
    let bin = num.toString(2)
    for(let i = 1; i < bin.length; i++){
        if(bin[i] != "0") return false
    }
    if( bin.length % 2) return true
    return false
}

Q. Given a positive binary integer, convert it to a decimal form.

Examples:

Given: 1101, returns 13

A.
function solution(n: number): number {
    return parseInt(n.toString(), 2)
}


Q. Given an integer, where each ith digit is represented by digits[i], add one and return its resulting array of digits. You may assume there is no leading zero(s) in an input array.

A.
function solution(digits: number[]): number[] {
    return (parseInt(digits.join('')) + 1).toString().split('').map(e => parseInt(e))
}


Q. Given a positive decimal integer, convert it to a hexadecimal form as a string.

A.
function solution(n: number): string {
    return n.toString(16).toUpperCase()
}


Q. Given an integer, return the sum of all digits until the sum reaches a digit of 1.

Examples:

Given: nun = 123 // returns 6

Explanation: 1 + 2+ 3 = 6

Given: nun = 49 // returns 4

Explanation: 4 + 9 = 13 --> 1+ 3 = 4

A.
function solution(num: number): number {
    while(num >= 10){
        num = num.toString().split('').map(e => parseInt(e)).reduce((a,b)=>a + b)
    }
    return num
}


Total time: 10 minutes
