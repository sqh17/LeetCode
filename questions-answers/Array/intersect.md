## 求两个数组的交集
    给定两个数组，编写一个函数来计算它们的交集。
#### 示例1
    输入: nums1 = [1,2,2,1], nums2 = [2,2]
    输出: [2,2]
#### 示例2
    输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
    输出: [4,9] 
#### 说明
    * 输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
    * 我们可以不考虑输出结果的顺序。
### 答案  ????
```  javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let i = j = 0,
        len1 = nums1.length,
        len2 = nums2.length,
        newArr = [];
    
    if( len1 === 0 || len2 === 0 ){
        return newArr;
    }
    
    nums1.sort((a,b)=>a - b);
    nums2.sort((a,b)=>a - b);
    
    while( i < len1 || j < len2 ){
        if( nums1[i] > nums2[j] ){
            j ++;
        }else if( nums1[i] < nums2[j] ){
            i ++;
        }else{
            if(nums1[i] === nums2[j]){
                newArr.push( nums1[i] );
            }
            if( i < len1 - 1 ){
                i ++;
            }else{
                break;
            }
            if( j < len2 - 1 ){
                j ++;
            }else{
                break;
            }
        }        
    } 
    return newArr;
};
```
### 答案 2  时间复杂度(O(n^2))
```  javascript
/**
 * @param {number[]} arr1
 * @param {number[]} arr2
 * @return {number[]}
 */
var intersect = function(arr1, arr2) {
    let arr  = []
    for(var i = 0;i<arr1.length;i++){
        for(var j = 0;j<arr2.length;j++){
            if(arr1[i] == arr2[j]){
                arr.push(arr1[i])
            }
        }
    }
    return [...new Set(arr)]
};
```
### 答案 3  时间复杂度(O(n))
```  javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    let map = new Map(),arr = [];
    nums1.forEach(item=>{
        map.set(item,true)
    })
    nums2.forEach(item=>{
        if(map.has(item)){
            arr.push(item)
        }
    })
    return [...new Set(arr)]
};
```
