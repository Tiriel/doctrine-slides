# ORM

<div class="h-lg vertical-content">

The ORM project serves as a link between your data classes and your database storage.

By means of system-agnostic entities, Doctrine will translate your data mapping to the storage and back again.

</div>

---

# Entities

<div class="h-lg vertical-content">

An Entity is the mapping configuration related to a PHP class:
This configuration is available in multiple formats:
* Attributes (recommended) or annotations (deprecated)
* Yaml
* XML
* PHP

</div>

---
layout: two-cols-header
---

# Entities

::left::

Mapping example:

::right::

```php
namespace App\Entity;

use App\Repository\BookRepository;
use Doctrine\ORM\Mapping as ORM;

#[ORM\Entity(repositoryClass: BookRepository::class)]
class Book
{
    #[ORM\Id]
    #[ORM\GeneratedValue]
    #[ORM\Column(type: 'integer')]
    private int $id;

    #[ORM\Column(type: 'string', length: 255)]
    private string $title;

    #[ORM\Column(type: 'decimal', precision: 5, scale: 2)]
    private float $price;

    public function getId(): ?int
    {
        return $this->id;
    }
    }
  	//...
}
```

---
layout: default
---

# New entity

You can create/update an entity by adding manually some mapping to a PHP class, or you can use the MakerBundle’s make:entity command to create both at the same time.

<div class="w-md h-1\/3 mx-auto vertical-content">

```bash
$ symfony console make:entity Book
```

</div>
