```php
<?php

namespace Github;

use DateTime;
use JsonSerializable;

class About implements JsonSerializable
{
    private string $name = "Abdellah Chadidi";
    private string $title = "Backend Developer & Entrepreneur";
    private string $currentProject = "Recroot.dev";
    private array $specialties = [
        "Backend Development 🖥️",
        "Scalability 🚀",
        "Code Quality ✅",
        "Performance Optimization ⚡"
    ];
    private array $technologies = [
        "Backend" => ["PHP", "Laravel", "Node.js"],
        "Frontend" => ["Vue.js", "Nuxt.js", "Flutter", "React"],
        "Cloud & DevOps" => ["AWS", "Docker", "Nginx", "Redis"],
        "Databases" => ["MySQL", "MariaDB", "MongoDB"]
    ];
    private array $notableWork = [
        "Airbit (1M+ users) 🎵",
        "Rwaq (4M+ users, incl. a streaming platform) 📺"
    ];
    private array $hobbies = ["Traveling ✈️", "Exploring Cafés ☕", "Building Cool Stuff 💡"];
    private string $email = "ac@recroot.dev";
    private string $twitter = "https://twitter.com/chadididev";

    public function __construct()
    {
        echo "👋 Hey there! I'm {$this->name}, a {$this->title}!\n";
    }

    public function getCurrentProject(): string
    {
        return "🔭 Currently building **{$this->currentProject}**, connecting companies with top-tier developers.";
    }

    public function getTechnologies(): string
    {
        return "🔧 Technologies I love: " . implode(", ", array_merge(...array_values($this->technologies))) . ".";
    }

    public function getNotableWork(): string
    {
        return "🚀 Notable projects: " . implode(" & ", $this->notableWork) . ".";
    }

    public function getHobbies(): string
    {
        return "🌍 Hobbies: " . implode(", ", $this->hobbies) . ".";
    }

    public function getContactInfo(): string
    {
        return "📫 Contact me at **{$this->email}** or on Twitter: [@chadididev]({$this->twitter})";
    }

    public function getDateInfo(): string
    {
        return "📅 Today is " . (new DateTime())->format('l, F j, Y') . ". Keep coding!";
    }

    public function jsonSerialize(): array
    {
        return [
            "name" => $this->name,
            "title" => $this->title,
            "currentProject" => $this->currentProject,
            "specialties" => $this->specialties,
            "technologies" => $this->technologies,
            "notableWork" => $this->notableWork,
            "hobbies" => $this->hobbies,
            "contact" => [
                "email" => $this->email,
                "twitter" => $this->twitter
            ],
            "date" => $this->getDateInfo()
        ];
    }
}

// Let's introduce myself 😎
$me = new About();
echo $me->getCurrentProject() . "\n";
echo $me->getTechnologies() . "\n";
echo $me->getNotableWork() . "\n";
echo $me->getHobbies() . "\n";
echo $me->getContactInfo() . "\n";
echo $me->getDateInfo() . "\n";

// JSON output for fun
echo json_encode($me, JSON_PRETTY_PRINT) . "\n";

```
