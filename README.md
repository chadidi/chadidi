```php
<?php

namespace Github;

use DateTime;

class About implements Person
{
    use HasStuffGoing;

    private string $name = 'Abdellah Chadidi';
    private string $title = 'Backend Developer & Entrepreneur';
    private string $currentProject = 'Recroot.dev';

    private array $specialties = [
        'Backend Development 🖥️',
        'Scalability 🚀',
        'Code Quality ✅',
        'Performance Optimization ⚡',
    ];

    private array $technologies = [
        'Backend' => ['PHP', 'Laravel', 'Node.js'],
        'Frontend' => ['Vue.js', 'Nuxt.js', 'Flutter', 'React'],
        'Cloud & DevOps' => ['AWS', 'Docker', 'Nginx', 'Redis'],
        'Databases' => ['MySQL', 'MariaDB', 'MongoDB'],
    ];

    private array $notableWork = [
        'Airbit (1M+ users) 🎵',
        'Rwaq (4M+ users, incl. a streaming platform) 📺',
    ];

    private array $hobbies = ['Traveling ✈️', 'Exploring Cafés ☕', 'Building Cool Stuff 💡'];
    private array $currentlyLearning = [];

    private string $email = 'ac@recroot.dev';
    private string $twitter = 'https://twitter.com/chadididev';

    public function __construct()
    {
        echo "👋 Hey there! I'm {$this->name}, a {$this->title}!\n";
    }

    public function addCurrentlyLearning(string $topic): void
    {
        $this->currentlyLearning[] = $topic;
    }

    // Other getters inside the trait!

    public function getDateInfo(): string
    {
        return "📅 Today is " . (new DateTime())->format('l, F j, Y') . ". Keep coding!";
    }

    public function getCurrentlyLearning(): string
    {
        return empty($this->currentlyLearning)
            ? "📖 Currently, I'm focusing on mastering new technologies and concepts."
            : "📖 Currently learning: " . implode(', ', $this->currentlyLearning) . ".";
    }
}

// Example Usage
$me = new About;
$me->addCurrentlyLearning('Go');
$me->addCurrentlyLearning('Prompt Engineering');

echo "\n" . $me->getCurrentlyLearning() . "\n";
echo $me->getContactInfo() . "\n";
echo $me->getDateInfo() . "\n";

```
