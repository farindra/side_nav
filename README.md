# side_nav
Katik Side nav modification with database in json value

//Controllers Set:
//================

use lukisongroup\models\system\side_menu\M1000;


public function actionIndex()
    {
        //set menu side menu index
        $side_menu=M1000::find()->findMenu('sss_berita_acara')->one()->jval;
        $side_menu=json_decode($side_menu,true);

        return $this->render('index',['side_menu'=>$side_menu]);
    }


//View Set with kartik side nav:
//==============================

use kartik\sidenav\SideNav;

<aside class="main-sidebar">
        <?php
        if (!Yii::$app->user->isGuest) {
            echo SideNav::widget([
                'items' => $side_menu,
                'encodeLabels' => false,
                //'heading' => $heading,
                'type' => SideNav::TYPE_DEFAULT,
                'options' => ['class' => 'sidebar-nav'],
            ]);
        };
        ?>
</aside>
