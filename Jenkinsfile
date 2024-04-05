//port 
//java -jar javaProject/products-java-api/target/products-java-api-1.0.0-SNAPSHOT.jar --spring.profiles.active=dev
import groovy.json.JsonSlurper
import groovy.json.JsonSlurperClassic 
pipeline{
    agent any
    environment{
        //api_url = "http://localhost:9999/products"
        api_url = "https://reqres.in/api/resource"
    }
    //parameters{
    //    string(name: 'stringParameter',defaultValue: 'something',description:'string paramter checking')
    //}
    stages{
        //node{
        stage("running the api"){
            steps{
                script{
                
                def geturl= "${api_url}"
                //def get= new url()
                sh "echo ${geturl}"
                //sh "echo ${params.stringParameter}"
                sh "echo starting the api request"
                //def response= httpRequest responseHandle: 'NONE', url: "${api_url}", wrapAsMultipart: false, Content-Type: 
                def response= httpRequest responseHandle: 'STRING', url: "${api_url}", validResponseCodes: '200', wrapAsMultipart: false
                //def json = new JsonSlurper().parseText(response.content)
                //def jsonx =  jsonParse(response.content)
                def jsonObj = readJSON text: response.content
                echo jsonObj.data.size().toString()
                

                /*sh "echo starting curl request"
                def output = sh(returnStdout: true,script: "curl -X GET -s localhost:9999/products").trim().tokenize("\n")
                def responseJson = readJSON text: output 
                //def json = new JsonSlurper().parseText(output)
                //def responseJson = readJSON text: json
                sh "echo ${responseJson}"*/
                    }
                }
            }
        //}
    }
}
def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}

/*
def response = sh(script: 'curl -X POST -H "Authorization:test" -H "content-type: multipart/form-data" https://api/upload', returnStdout: true)   
def responseObject = readJSON text: response
def ID = "$responseObject.id"
println("ID:  $ID")*/