.. index::
   single: Migration Classes

Migration Classes
=================

As now everything is setup and configured you are ready to start writing
migration classes. You can easily generate your first migration class with the
following command:

.. code-block:: bash

    $ ./doctrine migrations:generate
    Generated new migration class to "/path/to/migrations/classes/DoctrineMigrations/Version20100416130401.php"

Have a look and you will see a new class at the above location that looks like
the following:

.. code-block:: php

    namespace DoctrineMigrations;

    use Doctrine\DBAL\Migrations\AbstractMigration,
        Doctrine\DBAL\Schema\Schema;

    class Version20100416130401 extends AbstractMigration
    {
        public function up(Schema $schema)
        {

        }

        public function down(Schema $schema)
        {

        }
    }

Sometimes you need to do some complex migration operations which force you
to use plain SQL statements. Using the *addSql()* method this is possible within any
migration class.

First you need to generate a new migration class:

.. code-block:: bash

    $ ./doctrine migrations:generate
    Generated new migration class to "/path/to/migrations/DoctrineMigrations/Version20100416130422.php"

This newly generated migration class is the place where you can add your own
custom SQL queries:

.. code-block:: php

    namespace DoctrineMigrations;

    use Doctrine\DBAL\Migrations\AbstractMigration,
        Doctrine\DBAL\Schema\Schema;

    class Version20100416130422 extends AbstractMigration
    {
        public function up(Schema $schema)
        {
            $this->addSql('CREATE TABLE addresses (id INT NOT NULL, street VARCHAR(255) NOT NULL, PRIMARY KEY(id)) ENGINE = InnoDB');
        }

        public function down(Schema $schema)
        {
            $this->addSql('DROP TABLE addresses');
        }
    }
