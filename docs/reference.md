# Configuration Reference

## Resource Configuration Reference

```yaml
sylius_resource:
    resources:
        app.book:
            driver: doctrine/orm
            classes:
                model: # Required!
                interface: ~
                controller: Sylius\Bundle\ResourceBundle\Controller\ResourceController
                repository: ~
                factory: Sylius\Component\Resource\Factory\Factory
                form: Sylius\Bundle\ResourceBundle\Form\Type\DefaultResourceType
                    validation_groups: [sylius]
            options:
                object_manager: default
            templates:
                form: Book/_form.html.twig
            translation:
                classes:
                    model: ~
                    interface: ~
                    controller: Sylius\Bundle\ResourceBundle\Controller\ResourceController
                    repository: ~
                    factory: Sylius\Component\Resource\Factory\Factory
                    form: Sylius\Bundle\ResourceBundle\Form\Type\DefaultResourceType
                        validation_groups: [sylius]
                templates:
                    form: Book/Translation/_form.html.twig
                options: ~
```

## Routing Generator Configuration Reference

<details open><summary>Yaml</summary>

```yaml
app_book:
    resource: |
        alias: app.book
        path: library
        identifier: code
        criteria:
            code: $code
        section: admin
        templates: :Book
        form: App/Form/Type/SimpleBookType
        redirect: create
        except: ['show']
        only: ['create', 'index']
        serialization_version: 1
    type: sylius.resource
```

</details>

<details open><summary>PHP</summary>

```php

#[SyliusCrudRoutes(
    alias: 'app.book',
    path: 'library',
    identifier: 'code',
    criteria: [
        'code' => '$code',
    ],
    section: 'admin',
    templates: ':Book',
    form: SimpleBookType::class,
    redirect: 'create',
    except: ['show'],
    only: ['create', 'index'],
    serializationVersion: '1',
)]

```

</details>

**[Go back to the documentation's index](index.md)**
