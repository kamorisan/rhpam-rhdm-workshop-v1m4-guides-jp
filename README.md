Red Hat Process Automation Manager / Decision Manager Workshop Module 4
===
Red Hat Process Automation Manager と Red Hat Decision Manager の ハンズオンワークショップの `モジュール 4` です。
このワークショップでは、開発者や業務エキスパートに、最新のクラウドネイティブアーキテクチャのコンテキストでのルールおよびプロセス駆動型アプリケーションとマイクロサービスの紹介を行います。

Agenda
===
* イントロダクション
* Business Central ワークベンチ
* データソースの作成
* データセットの作成
* タスクレポートの作成
* 顧客満足度レポートの作成
* レポートの公開
* おわりに

Lab Instructions on OpenShift
===

APB経由で labs-infra をインストールした場合、ラボインストラクションはすでにデプロイされていることに注意してください。

ここでは、ラボインストラクションを OpenShift クラスタに手動でデプロイするための Ansible プレイブックの例を示します。
```
- name: Create Guides Module 4
  hosts: localhost
  tasks:
  - import_role:
      name: siamaksade.openshift_workshopper
    vars:
      project_name: "guide-m4"
      workshopper_name: "RHPAM / RHDM Workshop V1 Module-4"
      project_suffix: "-XX"
      workshopper_content_url_prefix: https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main
      workshopper_workshop_urls: https://raw.githubusercontent.com/kamorisan/rhpam-rhdm-workshop-v1m4-guides-jp/main/_rhpam-rhdm-workshop-module4.yml
      workshopper_env_vars:
        PROJECT_SUFFIX: "-XX"
        COOLSTORE_PROJECT: coolstore{{ project_suffix }}
        OPENSHIFT_CONSOLE_URL: "https://master.seoul-2922.openshiftworkshop.com"
        ECLIPSE_CHE_URL: "http://che-labs-infra.apps.seoul-2922.openshiftworkshop.com"
        GIT_URL: "http://gogs-labs-infra.apps.seoul-2922.openshiftworkshop.com"
        NEXUS_URL: "http://nexus-labs-infra.apps.seoul-2922.openshiftworkshop.com"
        LABS_DOWNLOAD_URL: "http://gogs-labs-infra.apps.seoul-2922.openshiftworkshop.com"

      openshift_cli: "/Users/doh/cloud-native-app-dev/oc --server https://master.seoul-2922.openshiftworkshop.com"
```
