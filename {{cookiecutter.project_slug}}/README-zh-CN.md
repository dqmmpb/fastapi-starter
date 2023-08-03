# fastapi-demo

## greenlet在M1芯片下不兼容问题

下载greenlet源码编译安装

```bash
git clone https://github.com/python-greenlet/greenlet
cd greenlet
python setup.py bdist_wheel
pip install dist/greenlet-3.0.0a2.dev0-cp310-cp310-macosx_11_0_arm64.whl
```


## poetry.lock中依赖版本问题

删除poetry.lock，更新 pyproject.toml中的依赖版本，更新`fastapi = "^0.100.0"`，重新安装依赖

```bash
poetry install
```


## frontend中react版本问题

删除yarn.lock，修改package.json为如下
```json
{
  "name": "frontend",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "build": "react-scripts build",
    "eject": "react-scripts eject",
    "format": "prettier src --write",
    "genapi": "openapi-generator-cli generate -i 'http://localhost:8000/api/v1/openapi.json' -g typescript-axios -o src/generated -p withSeparateModelsAndApi=true,apiPackage=api,modelPackage=models,useSingleRequestParameter=true",
    "open-e2e-test": "cypress open",
    "run-e2e-tests": "cypress run",
    "start": "react-scripts start",
    "test": "react-scripts test",
    "test:debug": "react-scripts --inspect-brk test --runInBand --no-cache"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest",
      "plugin:cypress/recommended"
    ]
  },
  "resolutions": {
    "@types/react": "17.0.2",
    "@types/react-dom": "17.0.2"
  },
  "dependencies": {
    "axios": "^0.21.4",
    "ra-data-json-server": "^4.12.2",
    "ra-data-simple-rest": "^4.12.2",
    "react": "^17.0.2",
    "react-admin": "^4.12.3",
    "react-dom": "^17.0.2",
    "web-vitals": "^3.4.0"
  },
  "devDependencies": {
    "@babel/plugin-proposal-private-property-in-object": "^7.21.11",
    "@openapitools/openapi-generator-cli": "^2.7.0",
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^12.1.5",
    "@testing-library/user-event": "^14.4.3",
    "@types/jest": "^29.5.3",
    "@types/node": "^20.4.2",
    "@types/react": "^17.0.2",
    "@types/react-dom": "^17.0.2",
    "@types/react-router": "^5.1.20",
    "cypress": "^12.17.1",
    "cypress-localstorage-commands": "^2.2.3",
    "eslint-plugin-cypress": "^2.13.3",
    "fork-ts-checker-webpack-plugin": "^6.5.3",
    "prettier": "^3.0.0",
    "react-scripts": "5.0.1",
    "typescript": "^5.1.6"
  }
}
```


## idea中使用.env文件

安装EnvFile插件，https://plugins.jetbrains.com/plugin/7861-envfile

