### Unnitests in JS

#### 0. Basic test with Mocha and Node assertion library

1. **Set up Mocha**:
   - Install Mocha: `npm install mocha --save-dev`.
   - Add a script to `package.json` for running tests: `"test": "mocha"`.

2. **Create `0-calcul.js`**:
   - Function `calculateNumber`:
     ```javascript
     function calculateNumber(a, b) {
       return Math.round(a) + Math.round(b);
     }
     module.exports = calculateNumber;
     ```

3. **Create `0-calcul.test.js`**:
   - Test cases using `assert`:
     ```javascript
     const assert = require('assert');
     const calculateNumber = require('./0-calcul');

     describe('calculateNumber', function() {
       it('should return 4 for inputs (1, 3)', function() {
         assert.strictEqual(calculateNumber(1, 3), 4);
       });

       it('should return 5 for inputs (1, 3.7)', function() {
         assert.strictEqual(calculateNumber(1, 3.7), 5);
       });

       it('should return 6 for inputs (1.5, 3.7)', function() {
         assert.strictEqual(calculateNumber(1.5, 3.7), 6);
       });

       it('should return 5 for inputs (1.2, 3.7)', function() {
         assert.strictEqual(calculateNumber(1.2, 3.7), 5);
       });
     });
     ```

4. **Run the test**:
   - Command: `npm test 0-calcul.test.js`.

#### 1. Combining descriptions

1. **Upgrade `calculateNumber` in `1-calcul.js`**:
   - Add `type` argument:
     ```javascript
     function calculateNumber(type, a, b) {
       a = Math.round(a);
       b = Math.round(b);

       if (type === 'SUM') return a + b;
       if (type === 'SUBTRACT') return a - b;
       if (type === 'DIVIDE') return b === 0 ? 'Error' : a / b;
     }
     module.exports = calculateNumber;
     ```

2. **Create `1-calcul.test.js`**:
   - Organize with `describe` and use `assert`:
     ```javascript
     const assert = require('assert');
     const calculateNumber = require('./1-calcul');

     describe('calculateNumber', function() {
       it('should return 6 for SUM (1.4, 4.5)', function() {
         assert.strictEqual(calculateNumber('SUM', 1.4, 4.5), 6);
       });

       it('should return -4 for SUBTRACT (1.4, 4.5)', function() {
         assert.strictEqual(calculateNumber('SUBTRACT', 1.4, 4.5), -4);
       });

       it('should return 0.2 for DIVIDE (1.4, 4.5)', function() {
         assert.strictEqual(calculateNumber('DIVIDE', 1.4, 4.5), 0.2);
       });

       it('should return "Error" for DIVIDE (1.4, 0)', function() {
         assert.strictEqual(calculateNumber('DIVIDE', 1.4, 0), 'Error');
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 1-calcul.test.js`.

#### 2. Basic test using Chai assertion library

1. **Copy and Modify Files**:
   - Copy `1-calcul.js` to `2-calcul_chai.js`.
   - Copy `1-calcul.test.js` to `2-calcul_chai.test.js`.

2. **Rewrite Tests Using Chai**:
   - Replace `assert` with `chai.expect`:
     ```javascript
     const { expect } = require('chai');
     const calculateNumber = require('./2-calcul_chai');

     describe('calculateNumber', function() {
       it('should return 6 for SUM (1.4, 4.5)', function() {
         expect(calculateNumber('SUM', 1.4, 4.5)).to.equal(6);
       });

       it('should return -4 for SUBTRACT (1.4, 4.5)', function() {
         expect(calculateNumber('SUBTRACT', 1.4, 4.5)).to.equal(-4);
       });

       it('should return 0.2 for DIVIDE (1.4, 4.5)', function() {
         expect(calculateNumber('DIVIDE', 1.4, 4.5)).to.equal(0.2);
       });

       it('should return "Error" for DIVIDE (1.4, 0)', function() {
         expect(calculateNumber('DIVIDE', 1.4, 0)).to.equal('Error');
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 2-calcul_chai.test.js`.

#### 3. Spies

1. **Create `utils.js`**:
   - Create `Utils` module:
     ```javascript
     const Utils = {
       calculateNumber: function(type, a, b) {
         a = Math.round(a);
         b = Math.round(b);

         if (type === 'SUM') return a + b;
         if (type === 'SUBTRACT') return a - b;
         if (type === 'DIVIDE') return b === 0 ? 'Error' : a / b;
       }
     };
     module.exports = Utils;
     ```

2. **Create `3-payment.js`**:
   - Function `sendPaymentRequestToApi`:
     ```javascript
     const Utils = require('./utils');

     function sendPaymentRequestToApi(totalAmount, totalShipping) {
       const result = Utils.calculateNumber('SUM', totalAmount, totalShipping);
       console.log(`The total is: ${result}`);
     }
     module.exports = sendPaymentRequestToApi;
     ```

3. **Create `3-payment.test.js`**:
   - Use `sinon.spy`:
     ```javascript
     const sinon = require('sinon');
     const Utils = require('./utils');
     const sendPaymentRequestToApi = require('./3-payment');

     describe('sendPaymentRequestToApi', function() {
       it('should call Utils.calculateNumber with SUM and log the total', function() {
         const spy = sinon.spy(Utils, 'calculateNumber');

         sendPaymentRequestToApi(100, 20);

         sinon.assert.calledOnceWithExactly(spy, 'SUM', 100, 20);
         spy.restore();
       });
     });
     ```

4. **Run the test**:
   - Command: `npm test 3-payment.test.js`.

#### 4. Stubs

1. **Copy and Modify Files**:
   - Copy `3-payment.js` to `4-payment.js`.
   - Copy `3-payment.test.js` to `4-payment.test.js`.

2. **Use Sinon Stubs**:
   - Modify the test to use `stub`:
     ```javascript
     const sinon = require('sinon');
     const Utils = require('./utils');
     const sendPaymentRequestToApi = require('./4-payment');

     describe('sendPaymentRequestToApi', function() {
       it('should call Utils.calculateNumber with SUM and log the total', function() {
         const stub = sinon.stub(Utils, 'calculateNumber').returns(10);
         const spy = sinon.spy(console, 'log');

         sendPaymentRequestToApi(100, 20);

         sinon.assert.calledOnceWithExactly(stub, 'SUM', 100, 20);
         sinon.assert.calledOnceWithExactly(spy, 'The total is: 10');

         stub.restore();
         spy.restore();
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 4-payment.test.js`.

#### 5. Hooks

1. **Copy and Modify Files**:
   - Copy `4-payment.js` to `5-payment.js`.
   - Copy `4-payment.test.js` to `5-payment.test.js`.

2. **Use Hooks**:
   - Modify test with `beforeEach` and `afterEach`:
     ```javascript
     const sinon = require('sinon');
     const Utils = require('./utils');
     const sendPaymentRequestToApi = require('./5-payment');

     describe('sendPaymentRequestToApi', function() {
       let spy;

       beforeEach(function() {
         spy = sinon.spy(console, 'log');
       });

       afterEach(function() {
         spy.restore();
       });

       it('should log the total as 120', function() {
         sendPaymentRequestToApi(100, 20);
         sinon.assert.calledOnceWithExactly(spy, 'The total is: 120');
       });

       it('should log the total as 20', function() {
         sendPaymentRequestToApi(10, 10);
         sinon.assert.calledOnceWithExactly(spy, 'The total is: 20');
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 5-payment.test.js`.

#### 6. Async tests with done

1. **Create `6-payment_token.js`**:
   - Function `getPaymentTokenFromAPI`:
     ```javascript
     function getPaymentTokenFromAPI(success) {
       return new Promise((resolve, reject) => {
        

 if (success) {
           resolve({ data: 'Successful response from the API' });
         } else {
           reject(new Error('Failed to get token'));
         }
       });
     }
     module.exports = getPaymentTokenFromAPI;
     ```

2. **Create `6-payment_token.test.js`**:
   - Test async with `done`:
     ```javascript
     const { expect } = require('chai');
     const getPaymentTokenFromAPI = require('./6-payment_token');

     describe('getPaymentTokenFromAPI', function() {
       it('should return a success message when success is true', function(done) {
         getPaymentTokenFromAPI(true)
           .then((response) => {
             expect(response).to.deep.equal({ data: 'Successful response from the API' });
             done();
           })
           .catch((error) => done(error));
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 6-payment_token.test.js`.

#### 7. Express app

1. **Create `7-index.js`**:
   - Basic Express server:
     ```javascript
     const express = require('express');
     const app = express();

     app.get('/', (req, res) => {
       res.send('Welcome to the payment system');
     });

     app.listen(7865, () => {
       console.log('API available on localhost port 7865');
     });

     module.exports = app;
     ```

2. **Create `7-index.test.js`**:
   - Test the Express server:
     ```javascript
     const request = require('supertest');
     const { expect } = require('chai');
     const app = require('./7-index');

     describe('GET /', function() {
       it('should return 200 and Welcome to the payment system', function(done) {
         request(app)
           .get('/')
           .expect(200)
           .end((err, res) => {
             expect(res.text).to.equal('Welcome to the payment system');
             done();
           });
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 7-index.test.js`.

#### 8. Route with parameters

1. **Modify `7-index.js` to `8-index.js`**:
   - Add route with parameter:
     ```javascript
     app.get('/cart/:id([0-9]+)', (req, res) => {
       const id = req.params.id;
       res.send(`Payment methods for cart ${id}`);
     });
     ```

2. **Create `8-index.test.js`**:
   - Test routes with and without valid parameters:
     ```javascript
     describe('GET /cart/:id', function() {
       it('should return 200 and Payment methods for cart 123', function(done) {
         request(app)
           .get('/cart/123')
           .expect(200)
           .end((err, res) => {
             expect(res.text).to.equal('Payment methods for cart 123');
             done();
           });
       });

       it('should return 404 for non-numeric id', function(done) {
         request(app)
           .get('/cart/abc')
           .expect(404, done);
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 8-index.test.js`.

#### 9. POST and json

1. **Create `9-index.js`**:
   - Add POST route to handle JSON:
     ```javascript
     app.post('/login', (req, res) => {
       const { userName } = req.body;
       res.send(`Welcome ${userName}`);
     });

     app.use(express.json());
     ```

2. **Create `9-index.test.js`**:
   - Test POST request:
     ```javascript
     describe('POST /login', function() {
       it('should return 200 and Welcome John Doe', function(done) {
         request(app)
           .post('/login')
           .send({ userName: 'John Doe' })
           .expect(200)
           .end((err, res) => {
             expect(res.text).to.equal('Welcome John Doe');
             done();
           });
       });
     });
     ```

3. **Run the test**:
   - Command: `npm test 9-index.test.js`.
