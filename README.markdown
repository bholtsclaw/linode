# Installation

    $ sudo pear install Net_URL2-0.3.1
    $ sudo pear install HTTP_Request2-0.5.2
    $ sudo pear channel-discover pear.keremdurmus.com
    $ sudo pear install krmdrms/Services_Linode
    
## Usage

    <?php
    require('Services/Linode.php');
    
    try {
        $linode = new Services_Linode('apikey');
        $a = $linode->linode_list();
        $b = $linode->domain_list(array('DomainID' => 23233));
        
        var_dump($a);
        var_dump($b);
    } catch (Services_Linode_Exception $e) {
        echo $e->getMessage();
    }
    ?>

#### To perform a batch request

    <?php
    require('Services/Linode.php');
    
    try {
        $linode = new Services_Linode('apikey');
        $linode->batching = true;
        $linode->linode_list();
        $linode->domain_list();
        $result = $linode->batchFlush();
        
        var_dump($result);
    } catch (Services_Linode_Exception $e) {
        echo $e->getMessage();
    }
    ?>

For more information about api methods visit <http://www.linode.com/api/autodoc.cfm>
