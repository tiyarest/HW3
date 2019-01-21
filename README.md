# HW3
练习一：
每次移动进度条都会调用onProgressChanged（）函数，在每次移动进度条都会调用onProgressChanged（）里对animationView进行修改
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                // TODO 3: 这里应该调用哪个函数呢
                float f = (float) progress /100;
                animationView.setProgress(f);
            }
  调用的setProgress（）
 public void setProgress(@FloatRange(from = 0f, to = 1f) final float progress) {
    if (composition == null) {
      lazyCompositionTasks.add(new LazyCompositionTask() {
        @Override public void run(LottieComposition composition) {
          setProgress(progress);
        }
      });
      return;
    }
    setFrame((int) MiscUtils.lerp(composition.getStartFrame(), composition.getEndFrame(), progress));
  }
  
 练习二：
 // TODO 1：在这里实现另一个 ObjectAnimator，对 target 控件的大小进行缩放，从 1 到 2 循环
        ObjectAnimator scaleX = ObjectAnimator.ofFloat(target, "scaleX", 1, 2f);
        scaleX.setDuration(Integer.parseInt(durationSelector.getText().toString()));
        scaleX.setRepeatCount(ObjectAnimator.INFINITE);
        scaleX.setRepeatMode(ObjectAnimator.REVERSE);

        ObjectAnimator scaleY = ObjectAnimator.ofFloat(target, "scaleY", 1, 2f);
        scaleY.setDuration(Integer.parseInt(durationSelector.getText().toString()));
        scaleY.setRepeatCount(ObjectAnimator.INFINITE);
        scaleY.setRepeatMode(ObjectAnimator.REVERSE);

        // TODO 2：在这里实现另一个 ObjectAnimator，对 target 控件的透明度进行修改，从 1 到 0.5f 循环
        ObjectAnimator alpha = ObjectAnimator.ofFloat(target,"alpha",1f,0.5f);
        alpha.setDuration(Integer.parseInt(durationSelector.getText().toString()));
        alpha.setRepeatCount(ObjectAnimator.INFINITE);
        alpha.setRepeatMode(ObjectAnimator.REVERSE);

        // TODO 3: 将上面创建的其他 ObjectAnimator 都添加到 AnimatorSet 中
        animatorSet = new AnimatorSet();
        animatorSet.play(animator1).with(scaleX).with(scaleY).with(alpha);
        animatorSet.start();
  
