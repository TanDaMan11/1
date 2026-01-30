# RLTrainer 🚀

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

**Easy Reinforcement Learning Bot Training for Rocket League**

RLTrainer is a Python application that simplifies the process of training custom Rocket League bots using reinforcement learning. No coding required - just input your reward weights and let the AI learn!

![RLTrainer Demo](https://img.shields.io/badge/Status-Active-green)

---

## 🎯 Features

- ✅ **No Coding Required** - Simple terminal interface for configuration
- ✅ **Fast Training** - Uses rlgym-sim (RocketSim) for headless training without the game
- ✅ **Flexible Rewards** - Customize exactly what behaviors your bot learns
- ✅ **Auto-Export** - Generates a complete, playable RLBot package
- ✅ **Checkpoint System** - Saves progress every 100k steps
- ✅ **Graceful Interruption** - Press Ctrl+C to stop early and still get your bot

---

## 📋 Table of Contents

- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Usage](#-usage)
- [Reward Configuration](#-reward-configuration)
- [Example Configurations](#-example-configurations)
- [Training Tips](#-training-tips)
- [Deployment](#-deployment)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

---

## ⚡ Quick Start

Get your first bot trained in under 30 minutes!

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/RLTrainer.git
cd RLTrainer

# 2. Install dependencies
pip install -r requirements.txt

# 3. Train your bot
python train_manager.py
```

**First-time recommended settings:**
- Bot Name: `MyFirstBot`
- Training Timesteps: `500000`
- Goal Reward: `10.0`
- Touch Reward: `0.1`
- Velocity to Ball: `0.5`
- Save Reward: `5.0`

---

## 🔧 Installation

### Prerequisites

- Python 3.8 - 3.11 (3.12+ may have compatibility issues)
- pip package manager
- 8GB+ RAM recommended
- NVIDIA GPU recommended (but not required)

### Setup

```bash
# Option A: Automatic setup (recommended)
python setup.py

# Option B: Manual install
pip install -r requirements.txt
```

### Verify Installation

```bash
# Check Python version
python --version

# Verify GPU (optional, for faster training)
python -c "import torch; print('GPU Available:', torch.cuda.is_available())"

# Run setup verification
python setup.py
```

---

## 🎮 Usage

### Basic Training

```bash
python train_manager.py
```

You'll be prompted to configure:

1. **Bot Name** - e.g., "MyBeastBot"
2. **Training Timesteps** - e.g., 1000000 (1 million)
3. **Reward Weights** - Configure behavior priorities

### Training Session Example

```
==============================================================
RLTrainer - Easy RL Bot Training for Rocket League
==============================================================

Enter bot name (e.g., 'MyBeastBot'): AggressiveBot
Enter training timesteps (e.g., 1000000): 1000000

------------------------------------------------------------
Reward Weights Configuration
------------------------------------------------------------
Goal scored reward (recommended: 10.0): 15
Ball touch reward (recommended: 0.1): 0.2
Velocity toward ball reward (recommended: 0.5): 1.0
Save reward (recommended: 5.0): 2.0

Proceed with training? (y/n): y
```

### During Training

- **Monitor Progress**: Watch terminal output for episode rewards
- **View Metrics**: `tensorboard --logdir=./tensorboard_logs`
- **Stop Early**: Press `Ctrl+C` (saves current progress)

---

## 🎯 Reward Configuration

The reward weights determine what behaviors your bot learns. Higher values = higher priority.

| Reward Type | Description | Recommended Range | Effect |
|-------------|-------------|-------------------|--------|
| **Goal** | Rewards scoring goals | 5 - 15 | Higher = More aggressive offense |
| **Touch** | Rewards touching the ball | 0.05 - 0.3 | Higher = More ball chasing |
| **Velocity to Ball** | Rewards moving toward ball | 0.3 - 1.5 | Higher = Faster approaches |
| **Save** | Rewards defensive saves | 2 - 12 | Higher = Better defense |

**Set a weight to 0 to disable that reward.**

---

## 📊 Example Configurations

### Quick Test (15-30 minutes)
```python
Timesteps: 500000
Goal: 10.0, Touch: 0.1, Velocity: 0.5, Save: 5.0
```

### Aggressive Offensive Bot (1-2 hours)
```python
Timesteps: 2000000
Goal: 15.0, Touch: 0.2, Velocity: 1.0, Save: 2.0
```

### Defensive Specialist (1-2 hours)
```python
Timesteps: 2000000
Goal: 5.0, Touch: 0.1, Velocity: 0.3, Save: 12.0
```

### Balanced All-Rounder (2-3 hours)
```python
Timesteps: 3000000
Goal: 10.0, Touch: 0.15, Velocity: 0.5, Save: 7.0
```

### Competition Bot (5+ hours)
```python
Timesteps: 10000000
Goal: 12.0, Touch: 0.15, Velocity: 0.6, Save: 8.0
```

**More configurations in [`example_configs.txt`](example_configs.txt)**

---

## 💡 Training Tips

### Performance Optimization

- **GPU Training**: 10x faster than CPU - highly recommended
- **Start Small**: Test with 500k timesteps first
- **Monitor Progress**: Watch episode rewards in terminal
- **Use Checkpoints**: Training saves every 100k steps

### Training Time Estimates

| Timesteps | GPU Time | CPU Time | Bot Quality |
|-----------|----------|----------|-------------|
| 100k | 5 min | 30 min | Barely moves |
| 500k | 15 min | 2 hours | Basic behavior |
| 2M | 45 min | 6 hours | Functional |
| 5M | 2 hours | 15 hours | Good |
| 10M+ | 4+ hours | 30+ hours | Very good |

### Best Practices

1. **Always test with 500k-1M timesteps first**
2. **Experiment with reward combinations**
3. **Be patient - good bots take time**
4. **Use example configs as starting points**
5. **Train overnight for competitive bots**

---

## 🚀 Deployment

After training completes, your bot will be in:
```
./exported_bots/YourBotName/
├── bot.py              # Bot inference code
├── bot.cfg             # RLBot configuration
├── appearance.cfg      # Car customization
├── model.zip           # Trained model weights
└── README.md           # Bot-specific instructions
```

### Using Your Bot

1. **Copy** the bot folder to your RLBot bots directory:
   - Windows: `C:\Users\YourName\AppData\Local\RLBotGUIX\RLBotPackManager\RLBot\bots\`

2. **Open** RLBot GUI

3. **Add** your bot to a match

4. **Play!** 🎮

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [README.md](README.md) | You are here! |
| [QUICKSTART.md](QUICKSTART.md) | 30-minute getting started guide |
| [TROUBLESHOOTING.md](TROUBLESHOOTING.md) | Solutions for common issues |
| [REFERENCE.md](REFERENCE.md) | Quick reference card |
| [PROJECT_OVERVIEW.md](PROJECT_OVERVIEW.md) | Technical architecture |
| [example_configs.txt](example_configs.txt) | Pre-made bot configurations |

---

## 🤝 Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Areas we'd love help with:
- Additional reward functions
- GUI interface
- Model comparison tools
- More documentation
- Bug fixes and optimizations

---

## 📈 Project Structure

```
RLTrainer/
├── train_manager.py          # Main training script
├── setup.py                  # Installation helper
├── requirements.txt          # Dependencies
├── README.md                 # This file
├── QUICKSTART.md            # Getting started guide
├── TROUBLESHOOTING.md       # Problem solving
├── REFERENCE.md             # Quick reference
├── example_configs.txt      # Example configurations
├── CONTRIBUTING.md          # Contribution guidelines
├── LICENSE                  # MIT License
│
├── checkpoints/              # Training checkpoints (created)
├── trained_models/           # Final model files (created)
├── exported_bots/            # Ready-to-use bots (created)
└── tensorboard_logs/         # Training metrics (created)
```

---

## 🔬 Technical Details

### Libraries Used

- **rlgym-sim**: Fast, headless Rocket League simulation using RocketSim
- **stable-baselines3**: Industry-standard RL algorithm implementations (PPO)
- **RLBot**: Framework for running custom bots in Rocket League
- **PyTorch**: Deep learning backend

### Algorithm

Uses **Proximal Policy Optimization (PPO)**, a state-of-the-art reinforcement learning algorithm proven effective for robotic control tasks.

---

## 🐛 Troubleshooting

**Training is slow?**
- Check GPU availability: `python -c "import torch; print(torch.cuda.is_available())"`
- Reduce timesteps for testing

**Bot doesn't move in RLBot?**
- Install dependencies in RLBot's Python environment
- Check RLBot logs for errors

**Module not found?**
- Run: `pip install -r requirements.txt`

**More help:** See [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

Built with:
- [rlgym-sim](https://github.com/AechPro/rlgym-sim) by AechPro
- [Stable-Baselines3](https://github.com/DLR-RM/stable-baselines3) by DLR-RM
- [RLBot](https://github.com/RLBot/RLBot) by the RLBot community

---

## 📞 Support

- **Issues**: Open an issue on GitHub
- **Questions**: Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
- **Documentation**: See [docs](#-documentation)

---

## ⭐ Star History

If you find this project helpful, consider giving it a star! ⭐

---

**Happy Training! 🎮🤖**

May your bots score many goals and make many saves!
