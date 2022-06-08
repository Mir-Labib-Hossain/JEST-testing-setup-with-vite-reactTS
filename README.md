# vite-reactTS-JEST-setup

src: https://egghead.io/lessons/jest-intro-to-confidently-testing-redux-applications-with-jest-typescript

run
npm install --save-dev jest-environment-jsdom
npm install -D jest                          
npm install -D @testing-library/react @testing-library/jest-dom @testing-library/user-event
npm install -D @babel/preset-react @babel/preset-typescript @babel/preset-env
npm install -D identity-obj-proxy


#########################
react-app/babel.config.js
-------------------------
module.exports = {
  presets: [
    [
      "@babel/preset-env",
      {
        targets: {
          node: "current",
        },
      },
    ],
    "@babel/preset-react",
    "@babel/preset-typescript",
  ],
};


#######################
react-app/jest-setup.ts
-----------------------
import "@testing-library/jest-dom"


######################
react-app/package.json
----------------------
{
   "scripts": {
    ...
    "test": "jest"
  },
  "devDependencies": {
    ...
  },
  "jest": {
    "testEnvironment": "jsdom",
    "setupFilesAfterEnv": [
      "<rootDir>/jest-setup.ts"
    ],
    "collectCoverage":true,
    "collectCoverageFrom": [
      "src/**/*.{ts,tsx,js,jsx}",
      "!src/**/*.d.ts"
    ],
    "moduleNameMapper": {
      "\\.(css|less)$": "identity-obj-proxy"
    }
  }
}


##########################
react-app/src/App.test.tsx
--------------------------
it("this jest is working",()=>{
    expect(true).toBe(true)
})
const a = 2
export default a;


###
run
---
npm test -- --coverage   
