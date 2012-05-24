---
layout: post
title: "Rails many-to-many recursion"
date: 2012-05-24 15:00
comments: true
categories: rails activerecord migration recursion many
---

googled for a while, determine to roll out my own version.

### The Problem
We have a product, which can acts as material for other products, thus a product can has_many products, at the same time, products are composed by many other products, so a product can also has_many materials(product).

### Solve
Product migration file

    class CreateProducts < ActiveRecord::Migration
      def change
        create_table :products do |t|
          t.string  :name
        end
      end
    end

ProductShip migration file

    class CreateProductShips < ActiveRecord::Migration
      def change
        create_table :product_ships do |t|
          t.integer :product_id
          t.integer :material_id
        end
      end
    end

Model ProductShip

    class ProductShip < ActiveRecord::Base
      belongs_to :product
      belongs_to :material, :class_name => 'Product'
    end

Model Product

    class Product < ActiveRecord::Base
      has_many :materials, :class_name => 'ProductShip', :foreign_key => 'material_id'
      has_many :products, :class_name => 'ProductShip'
    end

That's it!! Not that hard isn't it ;)
