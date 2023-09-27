#Problem Statement - Area Calculator

Ron wishes to renovate his barn. He thinks that creating fences and keeping the animals separately would help him feed the animals easily and solve the problem of animals getting mixed. For this, he plans to divide the area into three parts. He will create a square area for the chickens, a circular area for the ducks and a rectangular area for the cows.​

Write an area calculator application to calculate the area of a square, rectangle, and circle that will help Ron design the fences.

const pi = 3.14;
```javascript
  const calculateArea = (choice, side, length, breadth, radius) => {
    let area = 0.0;
    // write logic here
    // note that you check the values passed are not null before performing any operation on them
    switch (choice) {
        case 'square':
            if (side > 0) {
                area = side * side;
            } else {
                area = -1; // Return -1 for invalid parameters
            }
            break;
        case 'rectangle':
            if (length > 0 && breadth > 0) {
                area = length * breadth;
            } else {
                area = -1; // Return -1 for invalid parameters
            }
            break;
        case 'circle':
            if (radius > 0) {
                area = pi * radius * radius;
            } else {
                area = -1; // Return -1 for invalid parameters
            }
            break;
        default:
            area = -1; // Return -1 for invalid choices
    }
    return area;
}
module.exports = { calculateArea }
```

```javascript
  Test Case - Chai

const chai = require('chai')
const expect = chai.expect
const calculateArea = require('../src/areacalculator').calculateArea

describe('Area Calculator',()=>{
    it('calculate area square',()=>{
        expect(calculateArea('square',5)).to.be.equal(20)
    })
    it('calculate area rectangle',()=>{
        expect(calculateArea('rectangle',0,4,6,0)).to.be.equal(24)
    })
    it('calculate area circle',()=>{
        expect(calculateArea('circle',0,0,0,4.5)).to.be.equal(63.585)
    })
    it('calculate area invalid choice',()=>{
        expect(calculateArea('cone')).to.be.equal(-1)
    })
    it('calculate area invalid square parameters',()=>{
        expect(calculateArea('square')).to.be.equal(-1)
    })
    it('calculate area invalid rectangle parameters',()=>{
        expect(calculateArea('rectangle')).to.be.equal(-1)
    })
    it('calculate area invalid circle parameters',()=>{
        expect(calculateArea('circle')).to.be.equal(-1)
    })
})
```

