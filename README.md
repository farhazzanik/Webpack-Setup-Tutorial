
** Now install node package so apply this command 
     
     npm init -y 


**Now we have to install some packages  so apply this command
    
    npm i -D webpack webpack-cli webpack-dev-server

**Next we have to install  bable related tools
	
	npm i -D @babel/core @babel/cli @babel/node @babel/polyfill @babel/preset-env @babel/register babel-loader babel-register html-webpack-plugin
	
	

**then create "index.html" file in main directory
**then create folder name as src and make and create one file as well name as "app.js"
**Next create a ".bablerc" in root directory and pasted this code and save file
				
		{
			"presets":[
				"@babel/preset-env"
			]
		}
**Next,create "webpack.config.js" file in root directory and copy this code and save file
	
			const path = require('path')
			const htmlWebpackPlugin = require('html-webpack-plugin')
			require('babel-register')

			module.exports = {
			    entry: ['@babel/polyfill', './src/app.js'], 
			    output: {
			        path: path.resolve(__dirname, 'dist'),
			        filename: 'bundle.js'
			    },

			    module: {
			        rules: [{

			            test: /\.js$/,
			            exclude: /node_modules/,
			            use: ['babel-loader']
			        }]
			    },

			    plugins: [
			        new htmlWebpackPlugin({
			            template: './index.html'
			        })
			    ],

			    mode: 'development',
			    devtool: 'inline-source-map',
			    devServer: {
			        open: true,
			        contentBase: '.dist'
			    }
			}

**Next  we have to change some code in "package.json" file,replace "package.json" code with this code


			{
			  "name": "webpack-Setup-Tutorial",
			  "version": "1.0.0",
			  "description": "",
			  "main": "index.js",
			  "scripts": {
			    "start" : "webpack-dev-server"
			  },
			  "repository": {
			    "type": "git",
			    "url": "git+https://github.com/farhazzanik/Webpack-Setup-Tutorial.git"
			  },
			  "keywords": [],
			  "author": "",
			  "license": "ISC",
			  "bugs": {
			    "url": "https://github.com/farhazzanik/Webpack-Setup-Tutorial/issues"
			  },
			  "homepage": "https://github.com/farhazzanik/Webpack-Setup-Tutorial#readme",
			  "devDependencies": {
			    "@babel/cli": "^7.7.0",
			    "@babel/core": "^7.7.2",
			    "@babel/node": "^7.7.0",
			    "@babel/polyfill": "^7.7.0",
			    "@babel/preset-env": "^7.7.1",
			    "@babel/register": "^7.7.0",
			    "babel-loader": "^8.0.6",
			    "babel-register": "^6.26.0",
			    "html-webpack-plugin": "^3.2.0",
			    "webpack": "^4.41.2",
			    "webpack-cli": "^3.3.10",
			    "webpack-dev-server": "^3.9.0"
			  }
			}


