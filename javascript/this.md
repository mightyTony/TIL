# this 
## 1.일반 함수의 this는 호출 위치에서 정의
## 2. 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의 

### 일반 함수안에 this 
const user = {
    firstName: 'Heropy',
    lastName: 'Park',
    age: 85,
    getFullName : function() {
        return `${this.firstName} ${this.lastName}`
    }
}

console.log(user.getFullName()) => Heropy Park

### 화살표 함수의 this
function user() {
    this.firstName = 'Neo'
    this.lastName = 'Anderson'

    return {
        firstName: 'Heropy',
        lastName: 'Park',
        age: 85,
        getFullName : () => {
            return `${this.firstName} ${this.lastName}`
        }
    }
}

const u = user()
console.log(u.getFullName) => Neo Anderson