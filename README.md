<h2>PMQuery</h2>

## Example Code
```php

<?php

namespace AustrianNoah\ExamplePlugin;

use austriannoah\libpmquery\PMQuery;
use austriannoah\libpmquery\PmQueryException;
use pocketmine\plugin\PluginBase;

class ExampleCode extends PluginBase {
    
    
    public function onEnable(): void
    {
        $this->querySomeServer();
    }
    
    private function querySomeServer(): void
    {
        try {
            $query = PMQuery::query("geo.hivebedrock.network", 19132);
            $onlinePlayers = (int) $query["OnlinePlayers"];
            $maxPlayers = (int) $query["MaxPlayers"];
            $hostName = (string) $query["HostName"];
            $this->getLogger()->info("Queried Hive Games");
            $this->getLogger()->warning("Online: " . $onlinePlayers);
            $this->getLogger()->warning("Max: " . $maxPlayers);
            $this->getLogger()->warning("Host: " . $hostName);
        } catch (PmQueryException $e) {
            $this->getLogger()->error($e->getMessage());
        }
    }
}

```

