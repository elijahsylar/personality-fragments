# Personality Fragments 🧠💬

A multi-agent conversation system where AI personalities with distinct traits engage in emergent dialogue, influencing each other's emotional states through interaction.

![Python](https://img.shields.io/badge/python-3.7+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Lines of Code](https://img.shields.io/badge/lines%20of%20code-<300-brightgreen.svg)

## Overview

Personality Fragments demonstrates how simple emotional models and personality traits can create complex, emergent conversational dynamics. Five distinct AI agents interact, each with their own personality style and emotional state that evolves based on the conversation.

### Key Features

- **5 Unique Personalities**: Each agent has a distinct conversational style
  - **Alex**: Analytical thinker who values logic and evidence
  - **Blake**: Creative soul who sees possibilities everywhere
  - **Casey**: Practical realist focused on implementation
  - **Dana**: Empathetic mediator who considers everyone's feelings
  - **Evan**: Contrarian challenger who questions assumptions

- **Dynamic Emotional States**: Four parameters that change during conversation
  - **Mood**: Ranges from negative (-1) to positive (1)
  - **Energy**: Low (0) to high (1) engagement level
  - **Confidence**: Uncertainty (0) to assertiveness (1)
  - **Openness**: Closed (0) to receptive (1) to new ideas

- **Emergent Behaviors**:
  - Confident agents naturally dominate conversations
  - Mood contagion affects group dynamics
  - Energy levels influence participation
  - Topics trigger different group behaviors

## Installation

```bash
# Clone the repository
git clone https://github.com/yelijahsylar/personality-fragments.git
cd personality-fragments

# No external dependencies required! Uses only Python standard library
python personality_fragments.py
```

## Usage

### Basic Example

```python
from personality_fragments import Agent, ConversationManager, PERSONALITIES

# Create agents with predefined personalities
agents = [Agent(name, personality) for name, personality in PERSONALITIES.items()]

# Initialize conversation manager
manager = ConversationManager(agents)

# Run a conversation
manager.run_conversation("artificial intelligence ethics", turns=8)
```

### Custom Personalities

```python
# Define your own personality
custom_personality = {
    "style": "philosophical",
    "base_mood": 0.3,
    "base_energy": 0.4,
    "base_confidence": 0.6,
    "base_openness": 0.9,
    "reaction_weights": {"mood": 0.7, "energy": 0.5},
    "templates": {
        "enthusiastic": ["The metaphysical implications of {topic} are profound!"],
        "pessimistic": ["But does {topic} truly address the human condition?"],
        "assertive": ["Philosophically speaking, {topic} represents..."],
        "curious": ["What is the essence of {topic}?"],
        "neutral": ["Let us contemplate {topic}"]
    }
}

# Create custom agent
philosopher = Agent("Sophia", custom_personality)
```

## Example Output

```
=== Topic: artificial intelligence ethics ===

Alex [mood:0.2, energy:0.6]: Based on the evidence, artificial intelligence ethics clearly shows
Let me analyze this: the data suggests

Blake [mood:0.7, energy:0.8]: Oh wow! artificial intelligence ethics opens up amazing possibilities!
What if we

Casey [mood:0.0, energy:0.5]: Look, artificial intelligence ethics needs concrete solutions
Practically speaking

Dana [mood:0.5, energy:0.4]: I worry about how artificial intelligence ethics affects everyone
I think artificial intelligence ethics means different things to different people

=== Final Emotional States ===
Alex: mood=0.15, energy=0.58, confidence=0.75, openness=0.45
Blake: mood=0.52, energy=0.72, confidence=0.48, openness=0.88
Casey: mood=-0.08, energy=0.45, confidence=0.68, openness=0.52
```

## How It Works

1. **Personality Definition**: Each agent has base emotional values and response templates
2. **Response Generation**: Agents select templates based on their current emotional state
3. **Emotional Influence**: Messages carry sentiment that affects other agents' states
4. **Turn Selection**: Probability of speaking based on energy and confidence levels
5. **State Evolution**: Emotional parameters update continuously throughout conversation

## Extending the System

### Add New Emotional Parameters
```python
@dataclass
class ExtendedEmotionalState(EmotionalState):
    curiosity: float = 0.5  # Add new parameter
    patience: float = 0.7
```

### Create Topic-Specific Behaviors
```python
def generate_response(self, context, topic):
    if "climate" in topic and self.personality['style'] == 'practical':
        # Special handling for specific topic-personality combinations
        return self.generate_urgent_response(topic)
```

### Implement Memory Systems
```python
class Agent:
    def __init__(self, name, personality):
        # ... existing code ...
        self.long_term_memory = []  # Add persistent memory
        self.relationships = {}     # Track relationships with other agents
```

## Contributing

Contributions are welcome! Some ideas for enhancement:

- Add more sophisticated NLP for sentiment analysis
- Implement relationship tracking between agents
- Create visualization of emotional states over time
- Add more personality archetypes
- Develop topic-specific expertise for agents

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by research in multi-agent systems and emergent behavior
- Built as a demonstration of how simple rules can create complex dynamics
- Designed to be educational and easily hackable

## Questions or Feedback?

Feel free to open an issue or submit a pull request. This project is meant to be a starting point for exploring multi-agent conversational dynamics!

---

*Built with ❤️ for those curious about emergent AI behaviors*
