function isObject(value){
  return Object.prototype.toString.call(value)==="[object Object]"
}
export function isFunction(value){
  return Object.prototype.toString.call(value)==="[object Function]"
}

function isArray(value){
  return Object.prototype.toString.call(value)==="[object Array]"
}

export function combineObject(oldObj = {}, newObj = {}) {
  const oldObject=Object.assign({},oldObj)
  const newObject=Object.assign({},newObj)
  for (let i in newObject) {
    if (isArray(newObject[i])) {
      oldObject[i]=combineArray(oldObject[i],newObject[i])
    }
    else if (isObject(newObject[i])) {
      oldObject[i] = combineObject(oldObject[i], newObject[i])
    }
    else {
      oldObject[i] = newObject[i]

    }
  }
  return oldObject


}
export function combineArray(oldAr = [], newAr = []) {
  const oldArray=oldAr.slice();
  const newArray=newAr.slice();
  newArray.forEach((elem,index) => {
    if (isObject(elem)) {
      oldArray[index] = combineObject(oldArray[index],elem)
    }
    else if (isArray(elem)) {
      oldArray[index]=combineArray(oldArray[index],elem)
    }
    else {
      oldArray[index] = elem
    }

  })
  return oldArray
}
