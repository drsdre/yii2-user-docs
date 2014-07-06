Overriding controllers
======================

Sometimes you may need to override default Yii2-user controllers. It is pretty easy and takes
two steps.

Step 1: Create new controller
-----------------------------

First of all you need to create new controller under your own namespace (e.g. app\controllers)
and extend it from needed Yii2-user controller.

For example, if you want to override AdminController you should create **app\controllers\AdminController**
and extend it from **dektrium\user\controllers\AdminController**:

.. code-block:: php

    <?php

    namespace app\controllers;

    use dektrium\user\controllers\AdminController as BaseAdminController;

    class AdminController extends BaseAdminController
    {
        public function actionCreate()
        {
            // do your magic
        }
    }

Step 2: Add your controller to controller map

To let Yii2-user know about your controller you should add it to controller map as follows:

.. code-block:: php

    <?php return [
        ...
        'modules' => [
            ...
            'user' => [
                'class' => 'dektrium\user\ModuleManager',
                'controllerMap' => [
                    'admin' => 'app\controller\AdminController'
                ],
                ...
            ],
            ...
        ],
