pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "JDK8"
    }
    stages {
        stage('チェックアウト') {
            steps {
                git 'https://github.com/mysd33/Jenkins_Practical_Guide_2nd_Edition.git'
            }
        }
        stage('Mavenビルド') {
            steps {
                bat "mvn clean package -s C:\\Users\\yoshidamss\\.m2\\settings.xml"
            }
        }
        stage('テスト結果の集計') {
            steps {
                junit('target/surefire-reports/*.xml')
                jacoco(execPattern: 'target/jacoco.exec')
            }
        }
        stage('コード解析の結果集計') {
            steps {
                checkstyle(pattern: 'target/checkstyle-result.xml')
                findbugs(pattern: 'target/findbugsXml.xml')
            }
        }
        
        
    }
    
}