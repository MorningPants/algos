Total time: 12 minutes

Q. Determine if the given string is a capital, satisfying one of the conditions:

All letters are capitals (e.g. "FORMATION")
Only the first character is a capital ("Formation")

function solution(s: string): boolean {
    if(s == s.toUpperCase()) return true;
    if(s[0] == s[0].toUpperCase() && s.substring(1) == s.substring(1).toLowerCase()) return true
    return false
}


Q. Given a substring sub and an input string full, remove all occurrences of sub from full.

**Input**: full: "abc" & sub: "ab"
**Expected Output**: "c"
**Input**: full: "ababab" & sub: "b"
**Expected Output**: "aaa"
**Input**: full: "abcabcabcabcabc" & sub: "abcba"
**Expected Output**: "abcabcabcabcabc"
because "abcba" appears in the 'full' string.

function solution(full: string, sub: string): string {
    if(sub == "") return full
    while(full.indexOf(sub) !== -1){
        let i = full.indexOf(sub)
        let j = i + sub.length
        full = full.substring(0, i) + full.substring(j)
    }
    return full
}


Given an array of strings, find the longest common prefix amongst those strings. If there is none, return "".

function solution(strs: string[]): string {
    let prefix = []
    let shortest = strs.reduce((a, b) => b.length <= a.length ? b : a)
    for(let i = 0; i < shortest.length; i++){
        let common = true
        for(let str of strs){
            if(str[i] !== shortest[i]){
                common = false
                break
            }
        }
        if(common) prefix.push(shortest[i])
    }
    return prefix.join('')
}


Q. Given a string, count the length of the last word. Words are separated more than one space.

Examples:

Given "I love programming" returns 11
Given " " returns 0

function solution(s: string): number {
    let arr = s.split(' ').filter(s => s.length > 0)
    return arr[arr.length - 1]?.length || 0
}


Q. Given two non-negative integers represented as string, return their sum

Examples:

Given "111" and "11" return "122"
Give "0" and "123" return "123"


function solution(s1: string, s2: string): string {
    // let[longstr, shortstr] = s1.length > s2.length ? [s1, s2] : [s2, s1]
    // let arr1 = longstr.split('').reverse()
    // let arr2 = shortstr.split('').reverse()
    // let newArr = []
    // let carry = 0
    // for(let i in arr2){
    //     let num = arr2[i]
        
    // }
    return (parseInt(s1) + parseInt(s2)).toString()
}


Given a string, your task is to replace each of its characters by the next one in the English alphabet; i.e. replace a with b, replace b with c, etc (z would be replaced by a).

Example

For inputString = "crazy", the output should be solution(inputString) = "dsbaz".

function solution(inputString: string): string {
    let alphabet = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','a']
    let arr = []
    for(let c of  inputString){
        arr.push(alphabet[alphabet.indexOf(c) + 1])
    }
    return arr.join('')
}
