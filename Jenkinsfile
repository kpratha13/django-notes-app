@Library("Shared") _
pipeline {

agent {label "amrita"}

stages{
    stage("Hello"){
        steps{
            script{
                hello()
            }
        }
    }
    stage("code"){
        steps{
           script{
               clone("https://github.com/kpratha13/django-notes-app.git" , "main")
           }
        }
    }
     stage("build"){
        steps{
            script{
             build("notes-app" , "latest" , "prathakhare")
            }
        }
    }
     stage("push to dockerhub"){
        steps{
             script{
                 push("notes-app" , "latest", "prathakhare")
             }
        }
    }
     stage("deploy"){
        steps{
             echo"this is deploying the code"
             sh "docker compose down && docker compose up -d "
        }
    }
  }
}
